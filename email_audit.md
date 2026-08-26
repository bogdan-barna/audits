# Email Notification Ecosystem Audit

> **Platform:** DreamJobs (HU/RO)
> **Audit Date:** 2026-05-26
> **Scope:** `dj` (Dashboard), `dj-api` (Backend API), `dj-nuxt` (Frontend)

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Repository Breakdown](#2-repository-breakdown)
3. [Master Email Matrix](#3-master-email-matrix)
4. [Deep Dive by Workflow](#4-deep-dive-by-workflow)
   - 4.1 [Authentication & Onboarding](#41-authentication--onboarding)
   - 4.2 [Job Applications](#42-job-applications)
   - 4.3 [Job Plans & Billing](#43-job-plans--billing)
   - 4.4 [Company Management](#44-company-management)
   - 4.5 [User Engagement & Marketing](#45-user-engagement--marketing)
   - 4.6 [DevChallenge (DC) Feature](#46-devchallenge-dc-feature)
   - 4.7 [SZMD (Year's Best Employer)](#47-szmd-years-best-employer)
   - 4.8 [Smart Bench Profile (SBP)](#48-smart-bench-profile-sbp)
   - 4.9 [Sharing & Referrals](#49-sharing--referrals)
   - 4.10 [Reviews](#410-reviews)
   - 4.11 [Admin & Miscellaneous](#411-admin--miscellaneous)
5. [Appendix: Regional Overriders](#5-appendix-regional-overriders)
6. [Appendix: Scheduled Commands Summary](#6-appendix-scheduled-commands-summary)

---

## 1. Executive Summary

### Architecture

Email delivery across the platform is handled by **two independent Laravel backends** (`dj` and `dj-api`), both of which use the **Laravel Notification / Mailable** system. The frontend (`dj-nuxt`) acts purely as a **BFF (Backend-for-Frontend) proxy** — it never sends email directly; it forwards HTTP requests to `dj-api` which then fires the appropriate event or notification.

```
┌──────────────┐  HTTP/JSON   ┌──────────────┐  Event/Notification    ┌──────────┐
│  dj-nuxt     │ ──────────►  │  dj-api      │ ─────────────────────► │  SMTP /  │
│  (Nuxt 3)    │              │  (Laravel)   │                        │  Mailgun │
└──────────────┘              └──────────────┘                        └──────────┘
                                                                              ▲
┌──────────────┐  Event/Notification / Direct Mail                            │
│  dj          │ ─────────────────────────────────────────────────────────────┘
│  (Laravel)   │
└──────────────┘
```

### Transport Layer

| Repo | Default Transport | Production Transport | Dev/Test Transport |
|---|---|---|---|
| `dj` | `MAIL_MAILER=smtp` | SMTP via `smtp.mailgun.org` (TLS :587) | Mailpit `:1025` |
| `dj-api` | `MAIL_MAILER=smtp` | SMTP via `smtp.mailgun.org` (TLS :587); `failover` fallback to `log` | Mailpit `:1025` |

Both repos also have a **Mailgun HTTP driver** (`'transport' => 'mailgun'`) configured in `config/mail.php` and Mailgun credentials (`MAILGUN_DOMAIN`, `MAILGUN_SECRET`) in `config/services.php`. The active transport is selected at runtime via `MAIL_MAILER` env variable.

### Dispatch Mechanism

All emails are dispatched through one of three patterns:

| Pattern | Where Used | Notes |
|---|---|---|
| **Laravel Notifications** (`$model->notify(new XyzNotification(...))`) | Both `dj` and `dj-api` | Preferred pattern. Most implement `ShouldQueue`. |
| **Mailable Classes** (`Mail::to(...)->send(new XyzMail(...))`) | `dj` only | Used for a handful of direct admin/B2B emails. |
| **Anonymous Notification Route** (`Notification::route('mail', $address)->notify(...)`) | Both | Used when recipient is not a database model (e.g., admin email addresses). |

### Queue

- **Development**: `QUEUE_CONNECTION=sync` — all notifications fire synchronously inline.
- **Production**: queue driver (`redis` / `database`) expected; most notifications implement `ShouldQueue` and the `Queueable` trait, meaning they are dispatched to the queue worker asynchronously.
- Many `dj` notifications also call `toDatabase()` / `toArray()` alongside `toMail()`, meaning they **persist in the `notifications` table** for in-app display as well as sending email.

---

## 2. Repository Breakdown

### 2.1 `dj` — Dashboard Application

**Role:** Admin/Employer-facing Laravel dashboard. Manages jobs, companies, billing, applicants.

**Mail-related directories:**

```
dj/app/
├── Mail/                          # 6 Mailable classes
│   ├── AppliedToJob.php
│   ├── AskForCareerAdvice.php
│   ├── CardPayment.php
│   ├── JobReview.php
│   ├── ShareLink.php
│   └── SzmdRedact.php
├── Notifications/                 # ~60 Notification classes
├── Listeners/
│   ├── Dashboard/                 # ~30 event listeners, many dispatch notifications
│   ├── Frontend/                  # ~10 listeners for job-seeker-initiated events
│   ├── Szmd/
│   └── ...
└── Providers/
    └── EventServiceProvider.php   # ~45 event → listener mappings
```

**Trigger mechanisms in `dj`:**

| Mechanism | Files | Notes |
|---|---|---|
| **Event → Listener → Notification** | `EventServiceProvider.php`, `Listeners/` | Primary pattern. Events fired in controllers/services, listeners dispatch notifications. |
| **Direct controller `->notify()`** | `UserController`, `AuthController`, `GoldEmailController`, `CandidateShortlistController`, `EgghunterController` | Ad-hoc triggers not fitting event model. |
| **Direct `Mail::to()->send()`** | `ShareViaMailController`, `JobApplication` listener, `SzmdRenominationListener`, `SzmdWithdrawnListener`, `SzamlazzhuInvoiceCreatedEventListener` | Mailable classes used for direct sends. |
| **Scheduled Console Commands** | `Console/Kernel.php` | ~15 commands that fire notification events or dispatch emails on a schedule. |

**Regional override system:** A `RegionClassResolver::resolve($baseClass)` utility selects between `dj/app/Notifications/XyzNotification.php` (HU default) and `dj/app/Overriders/RO/Notifications/XyzNotification.php` (RO market) at runtime based on the company/user's region. See [Appendix 5](#5-appendix-regional-overriders).

---

### 2.2 `dj-api` — Backend API

**Role:** REST API consumed by `dj-nuxt`. Handles job seeker flows: registration, applications, password reset, profile management.

**Mail-related directories:**

```
dj-api/app/
├── Notifications/                 # 11 Notification classes
│   ├── ApplicationB2bNotification.php
│   ├── ApplicationB2cNotification.php
│   ├── ApplicationB2cWithoutCompanyNotification.php
│   ├── CandidateShortlistNotification.php
│   ├── EmailValidationNotification.php
│   ├── JobNotificationSubscribeNotification.php
│   ├── OtpNotification.php
│   ├── PasswordResetNotification.php
│   ├── ProfileDeletionNotification.php
│   ├── SbpProfileCreatedNotification.php
│   └── WelcomeNotification.php
├── Listeners/                     # 8 event listeners
└── Providers/
    └── EventServiceProvider.php   # 6 event → listener mappings
```

**`dj-api` EventServiceProvider mappings:**

```php
Registered::class => [
    EmailVerificationListener::class,   // → EmailValidationNotification
    WelcomeNotificationListener::class, // → WelcomeNotification
],
ApplicationCreated::class => [
    ApplicationB2CNotificationListener::class, // → ApplicationB2c[WithoutCompany]Notification
    ApplicationB2BNotificationListener::class, // → ApplicationB2bNotification
    ApplicationSubscribeToMiniCRMListener::class,
],
PasswordResetEvent::class => [
    PasswordResetListener::class, // → PasswordResetNotification
],
ProfileDeleted::class => [
    SendProfileDeletionNotification::class, // → ProfileDeletionNotification
],
CVUploaded::class => [
    SendCVToN8NListener::class, // Non-email: forwards CV to n8n workflow
],
```

**Email templates (Blade):**

```
dj-api/resources/views/mail/
├── application_b2b.blade.php
├── application_b2c.blade.php
├── application_b2c_without_company.blade.php
├── candidate_shortlist.blade.php
├── job-notification.blade.php
├── otp.blade.php
├── password-reset.blade.php
├── profile_deleted.blade.php
└── welcome.blade.php
```

---

### 2.3 `dj-nuxt` — Frontend Application

**Role:** Nuxt 3 SSR frontend for job seekers. Does **not** send email directly. All user actions that trigger emails flow through server-side API proxy routes to `dj-api`.

**Server routes that initiate email-triggering API calls:**

```
dj-nuxt/server/api/
├── register.ts                    → POST /api/register      → dj-api fires Welcome + EmailValidation
├── forgot-password.ts             → POST /api/forgot-password → dj-api fires PasswordReset
├── reset-password.ts              → POST /api/reset-password  (no email, just sets password)
├── otp-request.post.ts            → POST /api/otp-request   → dj-api fires OtpNotification
├── remove-user.ts                 → DELETE /api/profile     → dj-api fires ProfileDeletion
├── application.ts                 → POST /api/jobs/{slug}/application → dj-api fires B2C+B2B notifications
├── application-without-auth.ts    → POST /api/jobs/{slug}/application (guest) → same
├── csl-order.ts                   → POST /api/candidate-shortlist → dj-api fires CandidateShortlist
└── minicrm-subscribe.ts           → (CRM only, no direct email)
```

---

## 3. Master Email Matrix

> **Legend:** ✅ Queued (async) | ⚡ Sync | 📅 Scheduled

| # | Trigger Event | Origin Repo | Handling Component / File | Recipient | Email Type | Template / Class |
|---|---|---|---|---|---|---|
| **AUTHENTICATION & ONBOARDING** | | | | | | |
| 1 | User registers via Nuxt | `dj-nuxt` → `dj-api` | `WelcomeNotificationListener` → `WelcomeNotification` | New user | Transactional — Welcome | `mail.welcome` ✅ |
| 2 | User registers via Nuxt | `dj-nuxt` → `dj-api` | `EmailVerificationListener` → `EmailValidationNotification` | New user | Transactional — Email Verification | `mail.email_validation` ✅ |
| 3 | User requests password reset (Nuxt) | `dj-nuxt` → `dj-api` | `PasswordResetListener` → `PasswordResetNotification` | User | Transactional — Password Reset | `mail/password-reset.blade.php` ✅ |
| 4 | User requests OTP login (Nuxt) | `dj-nuxt` → `dj-api` | `OtpNotification` (direct controller) | User | Transactional — OTP Code | `mail/otp.blade.php` ✅ |
| 5 | User registers via dj (legacy/dashboard) | `dj` | `RegisteredEventListener` → `UserRegistered` | New user | Transactional — Welcome | `mail.welcome` ✅ |
| 6 | Email validation re-send (dj) | `dj` | `UserController` → `EmailValidationNotification` | User | Transactional — Email Verification | `mail.email_validation` ✅ |
| 7 | New dashboard manager account created | `dj` | `CompanyManagerCreated` listener → `ActivateAddedAccountNotification` | New manager | Transactional — Account Activation | `mail.activateaddedaccount` ✅ |
| 8 | Manager account activated by admin | `dj` | `ManagerActivated` listener → `ManagerActivatedNotification` | Manager | Transactional — Activation Confirmed | `mail.manageractivated` ✅ |
| 9 | Manager registered/invited to company | `dj` | `ManagerRegistered` listener → `ManagerWelcomeNotification` | Manager | Transactional — Manager Welcome | `mail.managerwelcome` ✅ |
| **JOB APPLICATIONS** | | | | | | |
| 10 | Job application submitted (Nuxt, B2C) | `dj-nuxt` → `dj-api` | `ApplicationB2CNotificationListener` → `ApplicationB2cNotification` | Applicant (job seeker) | Transactional — Application Confirmation | `mail/application_b2c.blade.php` ✅ |
| 11 | Job application submitted (Nuxt, hidden company) | `dj-nuxt` → `dj-api` | `ApplicationB2CNotificationListener` → `ApplicationB2cWithoutCompanyNotification` | Applicant | Transactional — Application Confirmation (no company) | `mail/application_b2c_without_company.blade.php` ✅ |
| 12 | Job application submitted (Nuxt, B2B) | `dj-nuxt` → `dj-api` | `ApplicationB2BNotificationListener` → `ApplicationB2bNotification` | Company (job owner) | Transactional — New Application Alert | `mail/application_b2b.blade.php` ✅ |
| 13 | Job application submitted (dj legacy) | `dj` | `Frontend\JobApplication` listener → `AppliedToJob` Mailable | Applicant | Transactional — Application Confirmation | `mail.applied_to_job` (Markdown) ⚡ |
| 14 | Application rejected by company | `dj` | `ApplicationRejected` event → `ApplicationRejectedListener` → `ApplicationRejectedNotification` | Applicant | Transactional — Rejection | `mail.application_rejected` ✅ |
| 15 | Post-application survey (scheduled) | `dj` | `SendAppliedToJobSurveyEmail` command → `AppliedToJobSurveyNotification` | Applicant | Engagement — Survey | `mail.applied_to_job_survey` 📅 |
| 16 | Unfinished job application reminder (scheduled) | `dj` | `SendUnfinishedJobApplicationsNotification` command → `UnfinishedJobApplicationNotification` | Job seeker | Engagement — Re-engagement | `mail.unfinished-job-application` 📅 |
| **JOB PLANS & BILLING** | | | | | | |
| 17 | Job plan pending payment initiated | `dj` | `JobPlanPendingCreated` event → `JobPlanPendingCreatedNotification` | Company | Transactional — Pending Payment | `mail.jobplanpendingcreated` ✅ |
| 18 | Pending payment succeeded | `dj` | `JobPlanPendingSuccess` event → `JobPlanPendingSuccessNotification` | Company | Transactional — Payment Success | `mail.jobplanpendingsuccess` ✅ |
| 19 | Pending payment failed | `dj` | `JobPlanPendingFailed` event → `JobPlanPendingFailedNotification` | Company | Transactional — Payment Failed | `mail.jobplanpendingfailed` ✅ |
| 20 | Job plan expiring soon (scheduled) | `dj` | `ManageJobPlans` command → `JobPlanExpires` event → `JobPlanExpiresNotification` | Company | Alert — Expiry Warning | `mail.jobplanexpires` 📅✅ |
| 21 | Job plan expired (scheduled) | `dj` | `ManageJobPlans` command → `JobPlanExpired` event → `JobPlanExpiredNotification` | Company | Alert — Plan Expired | `mail.jobplanexpired` 📅✅ |
| 22 | Job closed when plan expired | `dj` | `JobPlanExpired` listener → `JobClosedNotification` | Company | Alert — Job Closed | `mail.closed_job_mail_to_b2b` 📅✅ |
| 23 | Job plan auto-closed by system | `dj` | `JobPlanAutoClosed` event → `JobPlanAutoClosedNotification` | Company | Alert — Auto-Closed | `mail.jobplanautoclosed` 📅✅ |
| 24 | Job plan upgrade offer (scheduled) | `dj` | `SendJobPlanUpgradeEmail` command → `JobPlanUpgrade` | Company | Marketing — Upgrade Offer | `mail.job_plan_upgrade` 📅 |
| 25 | Invoice created (Számlázz.hu webhook) | `dj` | `SzamlazzhuInvoiceCreated` event → `SzamlazzhuInvoiceCreatedEventListener` → `InvoiceNotification` | Company | Transactional — Invoice | `mail.invoice` / `mail.invoicerequest` ✅ |
| 26 | Invoice created — admin copy | `dj` | Same listener → `CardPayment` Mailable | Admin/finance team | Transactional — Payment Admin Alert | `mail.admin_card_payment` ⚡ |
| 27 | Invoice with offer — admin copy | `dj` | Same listener → `OfferAdminNotification` | Admin | Transactional — Offer Invoice Admin | *(internal template)* ✅ |
| 28 | Payment request expires soon | `dj` | `PaymentRequestExpires` event → `PaymentRequestExpiresNotification` | Company | Alert — Payment Deadline Warning | `mail.paymentrequestexpires` ✅ |
| 29 | Payment request expired | `dj` | `PaymentRequestExpired` event → `PaymentRequestExpiredNotification` | Company | Alert — Payment Expired | `mail.paymentrequestexpired` ✅ |
| 30 | Payment settled (bank transfer confirmed) | `dj` | `PaymentSettledEvent` → `SendPaymentSettledEmailListener` → `PaymentSettledNotification` | Company | Transactional — Payment Confirmed | *(internal template)* ✅ |
| 31 | Used PP (pay-per-click) coupon | `dj` | `UsedPPCouponEvent` → `UsedPPCouponListener` → `UsedPPCouponNotification` | Company + Admin contacts | Transactional — Coupon Used Alert | *(internal template)* ✅ |
| 32 | Coupon expiring soon (scheduled) | `dj` | `CouponExpiresNotification` command → `CouponExpiresNotification` | Company | Alert — Coupon Expiry | `mail.coupon_expires` 📅 |
| **COMPANY MANAGEMENT** | | | | | | |
| 33 | Company registered | `dj` | `CompanyRegistered` event → `CompanyRegistered` listener → `CompanyRegisteredNotification` | Company (founding user) | Transactional — Company Welcome | `mail.company-registered` ✅ |
| 34 | New company admin assigned | `dj` | `NewCompanyAdminEvent` → `NewCompanyAdminListener` → `NewCompanyAdminNotification` | Admin / marketing (RO) | Alert — New Company Admin | *(internal template)* ✅ |
| 35 | Company manager added to company | `dj` | `CompanyManagerAdded` event → `CompanyManagerAdded` listener → `CompanyManagerAddedNotification` | New manager | Transactional — Manager Invitation | `mail.manager_added` ✅ |
| 36 | Company manager removed | `dj` | `CompanyManagerRemoved` event → `CompanyManagerRemoved` listener → `CompanyManagerRemovedNotification` | Removed manager | Transactional — Removal Notice | `mail.managerremoved` ✅ |
| 37 | Job closed manually by admin | `dj` | `JobClosed` event → `JobClosed` listener → `JobClosedAdminNotification` | Admin contacts + marketing | Alert — Job Closed (internal) | `mail.admin_closed_job` ✅ |
| 38 | Job closed → notify all applicants | `dj` | `JobClosedToApplicants` event → `JobClosedToApplicants` listener → `JobClosedToApplicantsNotification` | All applicants of the job | Transactional — Job Closed Notice | `mail.closed_job_mail_to_applicants` ✅ |
| **USER ENGAGEMENT & MARKETING** | | | | | | |
| 39 | Job recommendation (daily/weekly, scheduled) | `dj` | `JobRecommendationNotifications` command → `JobRecommendationEvent` → `JobRecommendationListener` → `JobRecommendationNotification` | Job seeker (subscribed) | Marketing — Job Recommendations | `mail.recommended-jobs` 📅 |
| 40 | Saved job reminder (scheduled) | `dj` | `SavedJobReminder` command → `SavedJobReminderEvent` → `SavedJobReminderListener` → `SavedJobReminderNotification` | Job seeker | Engagement — Saved Job Alert | *(internal template)* 📅 |
| 41 | Job notification subscription (Nuxt/API) | `dj-nuxt` → `dj-api` | `AuthenticationController` → `JobNotificationSubscribeNotification` | Subscriber | Transactional — Subscription Confirmation | `mail/job-notification.blade.php` ⚡ |
| 42 | Unfinished profile reminder (scheduled) | `dj` | `UnfinishedProfileNotification` command → `UnfinishedProfileNotification` | Job seeker | Engagement — Profile Completion | *(internal template)* 📅 |
| 43 | B2B newsletter (scheduled) | `dj` | `SendB2BNotification` command → `B2BNotification` | B2B contact list | Marketing — Newsletter | `mail.b2b-newsletter` 📅 |
| 44 | Virtual bench newsletter (scheduled) | `dj` | `SendVirtualBenchNotification` / `VirtualBenchNotification` commands → `VirtualBench*Notification` | VB-subscribed job seekers | Marketing — VB Newsletter | *(internal templates)* 📅 |
| 45 | Lovable workplaces voting (scheduled) | `dj` | `SendLovableWorkplacesVotingNotification` command → `LovableWorkplacesVotingNotification` | Users | Marketing — Campaign | `mail.lovable-workplaces-voting` 📅 |
| 46 | Company blog post proposal | `dj` | `CompanyBlogPostProposalListener` → `CompanyBlogPostNotification` | Company | Engagement — Blog Proposal | `mail.company_blog_post` ✅ |
| 47 | Profile deleted confirmation | `dj-nuxt` → `dj-api` | `ProfileDeleted` event → `SendProfileDeletionNotification` → `ProfileDeletionNotification` | User | Transactional — Deletion Confirmed | `mail/profile_deleted.blade.php` ✅ |
| **DEVCHALLENGE (DC)** | | | | | | |
| 48 | New DevChallenge published (scheduled) | `dj` | `DcNewChallengeNewsletter` command → `DCNewChallengeNotification` | DC subscribers | Marketing — New Challenge | `mail.dc-new-challenge` 📅 |
| 49 | DC user activity milestone (scheduled) | `dj` | `DcActivityNewsletters` command → `DCUserActivationNotification` | DC user | Engagement — Activity | `mail.dc-activity` 📅 |
| 50 | DC user streak (scheduled) | `dj` | `DcStreakNotification` command → `DCUserStreakNotification` | DC user | Engagement — Streak | *(dc-activity variant)* 📅 |
| 51 | DC weekly results (scheduled) | `dj` | `DcWeeklyResultsNewsletter` command → `DCWeeklyResultsNotification` | DC subscribers | Marketing — Weekly Results | `mail.dc-weekly-results` 📅 |
| **SZMD (YEAR'S BEST EMPLOYER)** | | | | | | |
| 52 | Company nominates for SZMD award | `dj` | `SzmdRenominationListener` → `SzmdRedact` Mailable | Admin (business email) | Alert — SZMD Nomination | `mail.admin_szmd_redact` ⚡ |
| 53 | Company withdraws SZMD nomination | `dj` | `SzmdWithdrawnListener` → `SzmdRedact` Mailable | Company contact | Alert — SZMD Withdrawal | `mail.admin_szmd_redact` ⚡ |
| 54 | SZMD promo campaign | `dj` | `SzmdPromoNotification` | Companies/users | Marketing — SZMD Promo | *(internal template)* |
| **SMART BENCH PROFILE (SBP)** | | | | | | |
| 55 | SBP profile created | `dj-api` | `SbpProfileCreatedNotification` (controller/service) | User | Transactional — SBP Welcome | *(internal template)* ✅ |
| 56 | SBP PDF report ready (scheduled) | `dj` | `SendSbpPdfNotification` command → `SbpPdfNotification` | User | Transactional — PDF Ready | *(internal template)* 📅 |
| 57 | SBP search free credit awarded | `dj` | `SbpSearchFreeCreditNotification` | User | Engagement — Free Credit | *(internal template)* |
| 58 | SBP search lunch promo | `dj` | `SbpSearchLunchNotification` | User | Marketing — Promo | *(internal template)* |
| **SHARING & REFERRALS** | | | | | | |
| 59 | User shares a job/company via email | `dj` | `ShareViaMailController` → `Mail::to()->send(ShareLink)` | Friend (any email) | Engagement — Share | `mail.link_share_{modelType}` ⚡ |
| 60 | Friend invitation (IT quiz test) | `dj` | `TestController` → `FriendInviteNotification` | Friend | Engagement — Invite | `mail.tests_friend_invite` ⚡ |
| **REVIEWS** | | | | | | |
| 61 | Job review submitted | `dj` | `ReviewCreated` event → `ReviewCreatedEventListener` → `ReviewCreatedNotification` | Company | Transactional — New Review | *(internal template)* ✅ |
| 62 | Admin triggers job review email | `dj` | `Admin\JobReviewController` → `Notification::send()` → `ReviewCreatedNotification` | Company managers | Alert — Review Notification | *(internal template)* ⚡ |
| 63 | Admin submits user review | `dj` | `Admin\UserReviewController` → `UserReviewCreatedNotification` | User | Transactional — Review Received | *(internal template)* ⚡ |
| **ADMIN & MISC** | | | | | | |
| 64 | Gold profile interest submitted | `dj` | `GoldEmailController` → `GoldRequestNotification` | Admin (business) + Requester | Transactional — Gold Interest | `mail.gold_request_to_admin` / `mail.gold_request_to_b2b` ⚡ |
| 65 | Career advice request submitted | `dj` | `UserController` → `Mail::to()->send(AskForCareerAdvice)` | Admin (marketing) | Alert — Career Advice | `mail.admin_asked_for_career_advice` ⚡ |
| 66 | Candidate Shortlist service order (Nuxt) | `dj-nuxt` → `dj-api` | `CandidateShortlistController` → `CandidateShortlistNotification` | Admin (business team) | Alert — CSL Order | `mail/candidate_shortlist.blade.php` ⚡ |
| 67 | Candidate Shortlist service order (dj) | `dj` | `Api\CandidateShortlistController` → `CandidateShortlistNotification` | Admin (business) | Alert — CSL Order | `mail.candidate_shortlist` ⚡ |
| 68 | Egg hunt / Xmas promo | `dj` | `EgghunterController` → `EggHuntNotification` | Users / Companies | Marketing — Seasonal Promo | `mail.egghunt` ⚡ |

---

## 4. Deep Dive by Workflow

### 4.1 Authentication & Onboarding

#### 4.1.1 User Registration (via `dj-nuxt`)

```
1. User fills registration form in dj-nuxt
2. dj-nuxt/server/api/register.ts  ─POST /register──►  dj-api
3. dj-api AuthenticationController stores user, fires Registered event
4. EventServiceProvider dispatches two listeners:
   a. EmailVerificationListener  → $user->notify(new EmailValidationNotification)
      → Blade: mail/email_validation, subject: "mail.email-validation.subject"
   b. WelcomeNotificationListener → $user->notify(new WelcomeNotification)
      → Blade: mail/welcome, subject: region_trans('mail.welcome.subject')
5. Both notifications implement ShouldQueue → dispatched to queue worker
```

#### 4.1.2 Password Reset (via `dj-nuxt`)

```
1. User clicks "Forgot Password" in dj-nuxt
2. dj-nuxt/server/api/forgot-password.ts  ─POST /forgot-password──►  dj-api
3. dj-api fires PasswordResetEvent (with user model + token)
4. PasswordResetListener::handle() → resolves region class:
   - HU: PasswordResetNotification
   - RO: Overriders\RO\Notifications\PasswordResetNotification
5. $user->notify(new PasswordResetNotification($user, $token))
   → Blade: mail/password-reset.blade.php
   → Subject: "mail.password-reset.subject"
   → Contains a one-time reset URL with the token
```

#### 4.1.3 OTP Login (via `dj-nuxt`)

```
1. User requests OTP (passwordless login)
2. dj-nuxt/server/api/otp-request.post.ts  ─POST /otp-request──►  dj-api
3. dj-api controller creates OTP record, sends:
   $user->notify(new OtpNotification($user, $locale))
   → Blade: mail/otp.blade.php
   → Subject: "mail.otp.subject"
```

#### 4.1.4 Manager Onboarding (via `dj` dashboard)

```
1. Admin/company owner adds a new manager in the dashboard
   → Event: CompanyManagerCreated (new account created) or CompanyManagerAdded (existing user)
2a. CompanyManagerCreated → CompanyManagerCreated listener
    → $manager->notify(new ActivateAddedAccountNotification)
    → Template: mail.activateaddedaccount
    → Also sends notification to RO admin: Notification::route('mail', config('mail.addresses.ro'))
2b. CompanyManagerAdded → CompanyManagerAdded listener
    → $manager->notify(new CompanyManagerAddedNotification)
    → Template: mail.manager_added
3. When manager activates their account:
   Event: ManagerActivated → ManagerActivated listener
   → $user->notify(new ManagerActivatedNotification)
   → Template: mail.manageractivated
```

---

### 4.2 Job Applications

#### 4.2.1 Standard Application Flow (via `dj-nuxt`)

```
1. Job seeker submits application in dj-nuxt (with CV, optional cover letter)
2. dj-nuxt/server/api/application.ts  ─POST /jobs/{slug}/application──►  dj-api
3. dj-api ApplicationController stores the Application record, fires ApplicationCreated event
4. EventServiceProvider dispatches:
   a. ApplicationB2CNotificationListener:
      - Checks if job has hide_company flag
      - If hidden → $user->notify(new ApplicationB2cWithoutCompanyNotification)
        Template: mail/application_b2c_without_company.blade.php
      - Otherwise → $user->notify(new ApplicationB2cNotification)
        Template: mail/application_b2c.blade.php
      - Attaches CV and cover letter PDFs from storage/applications/
      - Also stores notification in `notifications` table (via='database')
   b. ApplicationB2BNotificationListener:
      - Resolves RO override if needed
      - $appRepository->notifyB2B(new ApplicationB2bNotification)
        → Sends to company managers/HR inbox
        Template: mail/application_b2b.blade.php
        Also attaches CV/cover letter
5. Both fire as queued jobs
```

#### 4.2.2 Application Rejection

```
1. Company manager clicks "Reject" on an applicant in dj dashboard
2. dj Dashboard\ApplicantController::notifyRejected()
   → fires ApplicationRejected event
3. ApplicationRejectedListener → resolves region class
   → $user->notify(new ApplicationRejectedNotification)
   Template: mail.application_rejected
```

---

### 4.3 Job Plans & Billing

#### 4.3.1 Job Plan Lifecycle Emails

The `ManageJobPlans` Artisan command runs on a schedule and checks plan statuses, firing the appropriate events.

```
Plan posted
  └── JobPlanPendingCreated event
        → JobPlanPendingCreatedNotification to Company
                "Your payment is pending"

Bank transfer received / card payment success
  └── JobPlanPendingSuccess event
        → JobPlanPendingSuccessNotification to Company
                "Payment confirmed, your job is active"

Payment fails
  └── JobPlanPendingFailed event
        → JobPlanPendingFailedNotification to Company

Plan active, nearing expiry (scheduled check)
  └── JobPlanExpires event
        → JobPlanExpiresNotification to Company
                "Your job plan expires in X days"

Plan expiry date passed (scheduled check)
  └── JobPlanExpired event
        → JobPlanExpiredNotification to Company
        → JobClosedNotification to Company (job was auto-closed)

System auto-closes job (no manual close)
  └── JobPlanAutoClosed event
        → JobPlanAutoClosedNotification to Company
```

#### 4.3.2 Invoice Flow (Számlázz.hu Integration)

```
1. Payment gateway (OTP SimplePay card / bank transfer) confirms payment
2. dj calls Számlázz.hu API to issue invoice
3. SzamlazzhuInvoiceCreated event fires
4. SzamlazzhuInvoiceCreatedEventListener::handle():
   a. Resolves InvoiceNotification (HU) or RO override
   b. If company has invoice_email configured:
        Notification::route('mail', $company->invoice_email)->notify(InvoiceNotification)
      Else:
        $company->notify(new InvoiceNotification)
        → Template: mail.invoice (szamla) or mail.invoicerequest (dijbekero/proforma)
   c. OfferAdminNotification to admin if invoice relates to a commercial offer
   d. Mail::to($notify)->send(new CardPayment($invoice))
        → Template: mail.admin_card_payment
        → Recipients: finance admin + company's DreamJobs contact + RO contact
```

---

### 4.4 Company Management

#### 4.4.1 Company Registration

```
1. Company submits registration in dj dashboard
2. Event: Dashboard\CompanyRegistered
3. CompanyRegistered listener → $company->notify(new CompanyRegisteredNotification)
   Template: mail.company-registered
   Region-overridden for RO market
```

#### 4.4.2 Manager Invitation / Removal

```
Add manager (existing user):
  CompanyManagerAdded event → CompanyManagerAdded listener
  → manager->notify(new CompanyManagerAddedNotification)
    + Notification::route(config('mail.addresses.ro'))->notify(...) [RO only]

Create manager (new account):
  CompanyManagerCreated event → CompanyManagerCreated listener
  → manager->notify(new ActivateAddedAccountNotification)

Remove manager:
  CompanyManagerRemoved event → CompanyManagerRemoved listener
  → manager->notify(new CompanyManagerRemovedNotification)
    Region-overridden for RO
```

#### 4.4.3 Job Closed – Applicants & Admin

```
Manual close by admin or expiry:
  JobClosed event → JobClosed listener:
    → Admin contacts notified: JobClosedAdminNotification
    → marketing email always notified

  JobClosedToApplicants event → JobClosedToApplicants listener:
    → Iterates job applications in chunks of 100
    → Each applicant: $user->notify(new JobClosedToApplicantsNotification)
      Template: mail.closed_job_mail_to_applicants
```

---

### 4.5 User Engagement & Marketing

#### 4.5.1 Job Recommendations (Scheduled)

```
Schedule: daily or weekly based on user subscription preference
Command: JobRecommendationNotifications
  → Fetches users subscribed to job recommendations
  → Fires JobRecommendationEvent per user (with matched job list)
  → JobRecommendationListener → $user->notify(new JobRecommendationNotification)
    Template: mail.recommended-jobs (daily) or mail.recommended-jobs-weekly
    Region-overridden for RO
```

#### 4.5.2 Job Notification Subscription (Nuxt/API)

```
User subscribes to job alerts without creating account:
  dj-nuxt/server/api/minicrm-subscribe.ts → dj-api
  OR dj-api AuthenticationController directly:
  → Notification::route('mail', [$email => $name])->notify(
        new JobNotificationSubscribeNotification($user, $password)
    )
    Template: mail/job-notification.blade.php
    Note: also sends temporary password if new account was created
```

#### 4.5.3 Saved Job Reminder (Scheduled)

```
Command: SavedJobReminder
  → Fetches users with saved jobs that are about to close / meet criteria
  → Fires SavedJobReminderEvent
  → SavedJobReminderListener → $user->notify(new SavedJobReminderNotification)
    Region-overridden for RO
```

---

### 4.6 DevChallenge (DC) Feature

The DevChallenge is a gamified coding contest feature. Emails are dispatched by scheduled Artisan commands in `dj`:

| Command | Notification | Description |
|---|---|---|
| `DcNewChallengeNewsletter` | `DCNewChallengeNotification` | Sent when a new challenge opens. `[DevChallenge]` subject prefix. |
| `DcActivityNewsletters` | `DCUserActivationNotification` | Activity / participation reminders for individual users. |
| `DcStreakNotification` | `DCUserStreakNotification` | Celebrates or reminds about active participation streaks. |
| `DcWeeklyResultsNewsletter` | `DCWeeklyResultsNotification` | Weekly recap of challenge results. |

All DC notifications use the `[DevChallenge]` subject prefix and target opted-in users only.

---

### 4.7 SZMD (Year's Best Employer)

SZMD ("Szuper Munkahely Díj") is an annual award for best employers.

```
Company nominates/re-nominates for SZMD:
  SzmdRenominationEvent → SzmdRenominationListener
  → Mail::to([config('mail.addresses.business')])->send(new SzmdRedact($company, true))
    Template: mail.admin_szmd_redact
    Subject: "mail.szmd-renominate.subject" (includes year config)

Company withdraws from SZMD:
  SzmdWithdrawnEvent → SzmdWithdrawnListener
  → Mail::to([$contactEmail])->send(new SzmdRedact($company, false))
    Template: mail.admin_szmd_redact
    Subject: "mail.szmd-redact.subject"
    Recipient: company's DreamJobs contact email
```

---

### 4.8 Smart Bench Profile (SBP)

SBP is a CV/profile feature for job seekers.

```
SBP profile created:
  → SbpProfileCreatedNotification dispatched (from API service/controller)
    Subject: "mail.sbp_profile_created.subject"

SBP PDF report generation (scheduled):
  Command: SendSbpPdfNotification
  → SbpPdfNotification to user
    PDF is a rendered CV template from dj-api/resources/views/cv_templates/

SBP search free credit:
  → SbpSearchFreeCreditNotification (ad-hoc, from service)

SBP search lunch promo:
  → SbpSearchLunchNotification (marketing campaign, manual trigger)
```

---

### 4.9 Sharing & Referrals

#### Share Link via Email

```
1. User clicks "Share via email" on a job or company page
2. dj ShareViaMailController::send()
   → Validates modelType (e.g., 'job', 'company')
   → Mail::to($request->send_to)->send(new ShareLink($modelType, $model, $sentBy))
     Template: mail.link_share_{modelType}  (e.g., mail.link_share_job)
     Subject: "mail.send-link-via-mail.subject" with sender's name
```

---

### 4.10 Reviews

```
Job review submitted by job seeker:
  ReviewCreated event → ReviewCreatedEventListener
  → $company->notify(new ReviewCreatedNotification($review, $actor))
    Notifies company managers about the new review

Admin manually sends review notification:
  Admin\JobReviewController::notify()
  → Notification::send($users, new ReviewCreatedNotification($review))

Admin creates user review:
  Admin\UserReviewController
  → $user->notify(new UserReviewCreatedNotification($user, $content))
```

---

### 4.11 Admin & Miscellaneous

#### Gold Profile Request

```
User submits interest in Gold Profile (premium service):
  GoldEmailController::send()
  → Notification::route('mail', config('mail.addresses.business'))
        ->notify(new GoldRequestNotification($request, 'admin'))
    Template: mail.gold_request_to_admin
    Subject: "mail.gold-request-b2b.subject"

  → Notification::route('mail', $request->email)
        ->notify(new GoldRequestNotification($request, 'b2b'))
    Template: mail.gold_request_to_b2b
    Subject: "GOLD Profil - Érdeklődés - {name}"
```

#### Career Advice Request

```
User submits career advice form:
  UserController::askForCareerAdvice()
  → Mail::to(config('mail.addresses.marketing'))->send(
        new AskForCareerAdvice($user, $name, $email, $files, $note)
    )
    Template: mail.admin_asked_for_career_advice
    Subject: "Karrier tanácsadás: {name}"
    Attaches any uploaded files
```

#### Candidate Shortlist (CSL) Order

```
Via Nuxt:
  dj-nuxt/server/api/csl-order.ts  ─POST /candidate-shortlist──►  dj-api
  dj-api CandidateShortlistController
  → Notification::route('mail', config('mail.addresses.business.{region}.address'))
        ->notify(new CandidateShortlistNotification($request))
    Template: mail/candidate_shortlist.blade.php
    Subject: "{name} - Candidate Shortlist megrendelés"

Via dj dashboard:
  dj Api\CandidateShortlistController
  → Same pattern, routed to config('mail.addresses.business')
```

#### Used PP Coupon (PPC Billing Alert)

```
When a company uses a pay-per-click coupon:
  UsedPPCouponEvent → UsedPPCouponListener
  1. $company->notify(new UsedPPCouponNotification(...))       ← to company
  2. foreach $notify as $email:
       Notification::route('mail', $email)                     ← to DJ contacts
           ->notify(new UsedPPCouponNotification(..., isAdmin=true))
  3. RO region: Notification::route('mail', config('mail.addresses.ro-marketing'))
                    ->notify(...) [marketing@dreamjobs.ro]
  Region-overridden for RO
```

---

## 5. Appendix: Regional Overriders

Both `dj` and `dj-api` implement a **regional class override system**. A `RegionClassResolver::resolve($baseClass)` utility returns the class name to instantiate based on the current region (HU vs RO).

### `dj` Overriders (`dj/app/Overriders/RO/`)

| Base Class | RO Override | Key Differences |
|---|---|---|
| `Notifications\ApplicationRejectedNotification` | ✅ | RO-specific template/subject |
| `Notifications\CompanyManagerRemovedNotification` | ✅ | RO-specific template |
| `Notifications\InvoiceNotification` | ✅ | RO VAT/fiscal rules |
| `Notifications\JobClosedNotification` | ✅ | RO language |
| `Notifications\JobClosedToApplicantsNotification` | ✅ | RO language |
| `Notifications\JobPlanExpiredNotification` | ✅ | RO language |
| `Notifications\JobRecommendationNotification` | ✅ | RO-specific logic |
| `Notifications\ManagerWelcomeNotification` | ✅ | RO onboarding content |
| `Notifications\NewCompanyAdminNotification` | ✅ | RO admin routing |
| `Notifications\SavedJobReminderNotification` | ✅ | RO language |
| `Notifications\UsedPPCouponNotification` | ✅ | RO billing/contacts |
| `Mail\CardPayment` | ✅ | RO invoice format |

### `dj-api` Overriders (`dj-api/app/Overriders/RO/`)

| Base Class | RO Override |
|---|---|
| `Notifications\ApplicationB2cWithoutCompanyNotification` | ✅ |
| `Notifications\PasswordResetNotification` | ✅ |
| `Notifications\WelcomeNotification` | ✅ |

---

## 6. Appendix: Scheduled Commands Summary

The following commands in `dj/app/Console/Kernel.php` are responsible for time-based email dispatch. Exact schedules (`->daily()`, `->weekly()`, etc.) are defined in the `schedule()` method of the Kernel.

| Command Class | Notification Dispatched | Audience | Frequency |
|---|---|---|---|
| `ManageJobPlans` | `JobPlanExpires`, `JobPlanExpired`, `JobPlanAutoClosed` events | Companies | Daily |
| `SendJobPlanUpgradeEmail` | `JobPlanUpgrade` | Companies with qualifying plans | Periodic |
| `SendAppliedToJobSurveyEmail` | `AppliedToJobSurveyNotification` | Applicants (N days after apply) | Daily |
| `SendUnfinishedJobApplicationsNotification` | `UnfinishedJobApplicationNotification` | Job seekers | Daily/Weekly |
| `UnfinishedProfileNotification` | `UnfinishedProfileNotification` | Job seekers | Periodic |
| `SavedJobReminder` | `SavedJobReminderNotification` | Job seekers | Periodic |
| `JobRecommendationNotifications` | `JobRecommendationNotification` | Subscribed job seekers | Daily/Weekly |
| `CouponExpiresNotification` | `CouponExpiresNotification` | Companies | Daily |
| `VirtualBenchNotification` / `SendVirtualBenchNotification` | `VirtualBench*Notification` | VB users | Periodic |
| `SendSbpPdfNotification` | `SbpPdfNotification` | SBP users | Periodic |
| `DcNewChallengeNewsletter` | `DCNewChallengeNotification` | DC subscribers | On new challenge |
| `DcActivityNewsletters` | `DCUserActivationNotification` | DC users | Periodic |
| `DcStreakNotification` | `DCUserStreakNotification` | DC users | Periodic |
| `DcWeeklyResultsNewsletter` | `DCWeeklyResultsNotification` | DC subscribers | Weekly |
| `SendB2BNotification` | `B2BNotification` | B2B contact list | Periodic |
| `SendLovableWorkplacesVotingNotification` | `LovableWorkplacesVotingNotification` | Users | Campaign-based |

---

*Document generated via automated codebase audit. Last updated: 2026-05-26.*
