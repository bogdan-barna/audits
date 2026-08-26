# Texte Email — Română (RO)

> **Platformă:** DreamJobs RO  
> **Sursă:** `dj/resources/lang/ro/mail.php` + `dj-api/lang/ro/mail.php`  
> **Ultima actualizare:** 2026-05-26  
> **Notă:** Marcajele `:placeholder` sunt date dinamice (ex. `:name`, `:company`, `:job`).  
> Tag-urile HTML provin din codul sursă original — emailurile sunt trimise în format HTML.

---

## Cuprins

1. [Înregistrare și Autentificare](#1-înregistrare-și-autentificare)
2. [Aplicații la Joburi](#2-aplicații-la-joburi)
3. [Planuri de Job și Facturare](#3-planuri-de-job-și-facturare)
4. [Gestionarea Companiei](#4-gestionarea-companiei)
5. [Engagement Utilizatori și Marketing](#5-engagement-utilizatori-și-marketing)
6. [DevChallenge](#6-devchallenge)
7. [Locuri de Muncă Iubibile (SZMD/Lovable Workplaces)](#7-locuri-de-muncă-iubibile-szmdelivrable-workplaces)
8. [Smart Bench Profile (SBP)](#8-smart-bench-profile-sbp)
9. [Distribuire și Invitații](#9-distribuire-și-invitații)
10. [Recenzii](#10-recenzii)
11. [Administrare și Altele](#11-administrare-și-altele)

---

## 1. Înregistrare și Autentificare

### 1.1 Email de bun venit (dj — utilizator dashboard)
**Sursă:** `dj/lang/ro/mail.php` → `welcome`  
**Șablon:** `mail.welcome`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe Dreamjobs! |

**Mesaj:**
> Bine ai venit! Noi, cei de la DreamJobs suntem foarte bucuroși, că ești alături de noi!
>
> Sperăm, că vei găsi rapid ceea ce dorești: muncă flexibilă, un office captivant, sau pur și simplu un salariu mai bun.
>
> Îți arătăm, unde găsești cele mai bune joburi:

**Semnătură:** Ținem pumnii, îți dorim succes în căutarea jobului perfect!

---

### 1.2 Email de bun venit (dj-api — înregistrare job seeker)
**Sursă:** `dj-api/lang/ro/mail.php` → `welcome`  
**Șablon:** `mail/welcome.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe DreamJobs! |

**Mesaj:**
> Bun venit la DreamJobs, ne bucurăm că ești alături de noi!
>
> Suntem siguri că vei găsi noul tău loc de muncă de vis în curând - fie că este vorba de un program de lucru flexibil, de o echipă sudată sau de oportunitatea de a avansa în carieră.
>
> Aruncă o privire în culisele companiilor și alege din pozițiile care ți se potrivesc:

**Bloc promo Self-Branding:**
> Dorim să te sprijinim eficient în căutarea unui loc de muncă, de aceea am creat soluția noastră unică pentru căutarea unui job. Profilul tău de Self-Branding te ajută să ieși în evidență față de alți candidați și să îți prezinți candidatura într-un mod autentic și convingător. Folosește instrumentele noastre creative pentru a arăta ce abilități te definesc și ce te face unic!

**CTA:** Văd joburile disponibile | Îmi creez profilul Self-Branding  
**Urare:** Îți ținem pumnii, mult succes în căutarea jobului perfect!  
**Ajutor:** Dacă te putem ajuta cu orice informație, scrie-ne un mail pe business@dreamjobs.ro.

---

### 1.3 Email de bun venit (dj-api — RO market, variantă specifică)
**Sursă:** `dj-api/lang/ro/ro-mail.php` → `welcome`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe DreamJobs Romania! |

**Mesaj:**
> Bine ai venit! Suntem foarte bucuroși, că ești alături de noi!
>
> Sperăm că vei găsi ceea ce dorești fie că este vorba de un program de lucru flexibil, de un birou pet friendly sau pur și simplu de un salariu atractiv.

**Ajutor:** business@dreamjobs.ro  
**Urare:** Îți ținem pumnii, îți dorim succes în căutarea jobului perfect!

---

### 1.4 Confirmare adresă email
**Sursă:** `dj/lang/ro/mail.php` → `email-validation` | `dj-api/lang/ro/mail.php` → `email-validation`  
**Șablon:** `mail.email_validation`

| Câmp | Conținut |
|---|---|
| **Subiect** | Confirmă-ți adresa de e-mail |

**Mesaj:**
> Felicitări, ai reușit să te înregistrezi! Mai ai un singur pas, te rugăm să confirmi adresa de email dând clic pe linkul de mai jos:

---

### 1.5 Solicitare resetare parolă (dj — dashboard)
**Sursă:** `dj/lang/ro/mail.php` → `password-reset.request`  
**Șablon:** `mail.passwordresetrequest`

| Câmp | Conținut |
|---|---|
| **Subiect** | Parolă uitată |
| **Titlu** | Schimbă parola |

**Mesaj:**
> Se pare că ai uitat parola profilului tău DreamJobs Romania.
>
> Nicio problemă, introdu o nouă parolă aici:

---

### 1.6 Parolă schimbată (dj — dashboard)
**Sursă:** `dj/lang/ro/mail.php` → `password-reset.success`

| Câmp | Conținut |
|---|---|
| **Subiect** | Parola ta a fost schimbată |

**Mesaj:**
> Ți-ai schimbat cu succes parola profilului tău DreamJobs Romania.

---

### 1.7 Resetare parolă (dj-api — job seeker)
**Sursă:** `dj-api/lang/ro/mail.php` → `password-reset`  
**Șablon:** `mail/password-reset.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Resetarea parolei |

**Mesaj:**
> Îți trimitem acest e-mail deoarece am primit o solicitare de resetare a parolei pentru contul tău.

**CTA:** Resetează parola  
**Informație:** Dacă nu ai solicitat resetarea parolei, nu este necesară nicio acțiune suplimentară.  
**Avertisment:** Acest link de resetare a parolei va expira în :count minute.

---

### 1.8 Cod OTP (cod de autentificare)
**Sursă:** `dj-api/lang/ro/mail.php` → `otp`  
**Șablon:** `mail/otp.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Cod de autentificare |

**Mesaj:**
> Folosește următorul cod din 6 cifre pentru a te autentifica în contul tău:

**Avertisment:** Acest cod este valabil :count minute.  
**Informație:** Dacă nu ai solicitat acest cod, te rugăm să ignori acest mesaj.

---

### 1.9 Confirmare abonare la notificări de joburi
**Sursă:** `dj-api/lang/ro/mail.php` → `job-notification`  
**Șablon:** `mail/job-notification.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ești abonat la alerta de joburi DreamJobs |

**Mesaj:**
> Dragă :name,
>
> Te-ai abonat cu succes la newsletter-ul nostru de alerte de joburi, deci ești cu un pas mai aproape de a-ți găsi noul loc de muncă.
>
> De acum înainte, îți vom trimite alerte de joburi personalizate pe baza ariei de interes selectate, pentru a te ajuta să găsești mai rapid următoarea ta mare oportunitate - fie că este vorba de un program de lucru flexibil, de un mediu de lucru inspirațional, de un birou pet-friendly sau de un pachet de beneficii mai atractiv.
>
> Parola ta temporară de acces: **:pw**
>
> Dacă simți că primești prea multe notificări, poți accesa cu ușurință setările tale, fie dând clic pe butonul Dezabonare din josul e-mailurilor noastre, fie CLICK AICI.
>
> În caz de întrebări, nu ezita să ne contactezi la :address.
>
> Îți dorim mult succes în căutarea jobului ideal!

---

## 2. Aplicații la Joburi

### 2.1 Aplicație reușită (B2C — confirmare pentru candidat, dj)
**Sursă:** `dj/lang/ro/mail.php` → `applied-to-job`  
**Șablon:** `mail.applied_to_job`

| Câmp | Conținut |
|---|---|
| **Subiect** | Felicitări! Ai aplicat cu succes la jobul: :company @ :job |

**Mesaj:**
> Felicitări, ai aplicat cu succes la poziția **:job** la compania **:company** prin DreamJobs.
>
> Compania a primit aplicația ta, te rugăm să ai răbdare! Dacă ai întrebări, scrie-ne la: :email

**Date partajate:** Am partajat cu ei următoarele informații, pentru a putea să te contacteze.

**Promo SBP:**
> **Știai că poți aplica la joburi și cu un profil de Self-branding la noi? Din 10 aplicații, în medie se acordă doar 2 interviuri. Îți mărești șansele prin profilul Self-branding - completează-l și aplică simplu data viitoare!**

**CTA-uri:**
- Uită-te la companiile la care recrutarea nu s-a oprit!
- Aplică și la celelalte joburi similare ale noastre!

**Urare:** Mult succes la căutarea jobului!

---

### 2.2 Aplicație reușită (B2C — confirmare pentru candidat, dj-api)
**Sursă:** `dj-api/lang/ro/mail.php` → `application-b2c`  
**Șablon:** `mail/application_b2c.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Felicitări! Ai aplicat cu succes la jobul: :company @ :job |
| **Subiect (fără companie)** | Felicitări! Ai aplicat cu succes la jobul: :job |

**Mesaj (standard):**
> Felicitări, ai aplicat cu succes la poziția **:job** la compania **:company** prin DreamJobs.
>
> Compania a primit aplicația ta, te rugăm să ai răbdare! Dacă ai întrebări, scrie-ne la: :email

**Mesaj (fără companie — hide_company):**
> Felicitări, ai aplicat cu succes la poziția **:job** prin DreamJobs.
>
> Compania a primit aplicația ta, te rugăm să ai răbdare!

**Recomandare parolă (pentru utilizatorii noi):**
> Trebuie doar să introduci o parolă și înregistrarea ta la DreamJobs este completă. Ulterior, vei putea aplica ușor la joburi și vei putea vizualiza oricând aplicațiile tale anterioare.
>
> Pentru a introduce o parolă și a finaliza înregistrarea ta DreamJobs, folosește linkul următor: link

**Promo SBP:**
> **Știai că poți aplica la joburi și cu un profil de Self-branding la noi? Din 10 aplicații, în medie se acordă doar 2 interviuri. Îți mărești șansele prin profilul Self-branding - completează-l și aplică simplu data viitoare!**

**CTA-uri:** Uită-te la companiile la care recrutarea nu s-a oprit! | Aplică și la celelalte joburi similare ale noastre!  
**Urare:** Mult succes la căutarea jobului!

---

### 2.3 Notificare nou candidat (B2B — pentru companie, dj-api)
**Sursă:** `dj-api/lang/ro/mail.php` → `application-b2b`  
**Șablon:** `mail/application_b2b.blade.php`

| Câmp | Conținut |
|---|---|
| **Subiect** | Candidat nou |

**Mesaj:**
> Avem vești grozave, **:name** a aplicat la poziția **:job** @ **:company**!!
>
> Vizualizați datele de candidatură și CV-ul lui **:name**!

**CTA:** Candidații jobului  
**PS:** Vă rugăm să îi trimiteți un răspuns în orice caz, chiar dacă candidatura nu este relevantă pentru acest job! Acest lucru este important nu numai pentru candidat, ci și pentru compania dvs. - un feedback adecvat face parte dintr-un brand angajator puternic.  
**Notă GDPR:** Vă rugăm să tratați datele candidaților primite în acest e-mail cu confidențialitate, în conformitate cu reglementările privind protecția datelor (GDPR) aplicabile.

---

### 2.4 Aplicație respinsă
**Sursă:** `dj/lang/ro/mail.php` → `application-rejected`  
**Șablon:** `mail.application_rejected`

| Câmp | Conținut |
|---|---|
| **Subiect** | Rezultatul candidaturii: :company @ :job |

**Mesaj:**
> Ne pare rău să te anunțăm că candidatura ta la poziția **:job** la compania **:company** nu a fost selectată.

**Încurajare:** Nu renunța! Te așteaptă alte oferte interesante de joburi care poate se potrivesc mai bine abilităților și obiectivelor tale de carieră.  
**CTA:** Văd joburile disponibile  
**Urare:** Mult succes la căutarea jobului!

---

### 2.5 Chestionar după aplicare la job
**Sursă:** `dj/lang/ro/mail.php` → `applied-to-job-survey`  
**Șablon:** `mail.applied_to_job_survey`

| Câmp | Conținut |
|---|---|
| **Subiect** | Abia așteptăm să auzim despre experiența ta de aplicare la job! :job |

**Mesaj:**
> Îți mulțumim că ai aplicat la un job prin site-ul nostru!
>
> Suntem curioși să auzim experiența ta, te rugăm să completezi acest scurt chestionar, ajută-ne cu munca noastră!

**CTA:** Completez chestionarul

---

### 2.6 Aplicație incompletă — memento
**Sursă:** `dj/lang/ro/mail.php` → `unfinished-job-application`

| Câmp | Conținut |
|---|---|
| **Subiect** | Continuați să aplicați |

**Mesaj:**
> Dragă :name,
>
> Se pare că încă nu ai finalizat aplicația ta pentru acest job. Nu uita să o trimiți înainte de expirarea anunțului!
>
> :job_name
>
> [LINK]

---

## 3. Planuri de Job și Facturare

### 3.1 Job publicat (după plată în așteptare)
**Sursă:** `dj/lang/ro/mail.php` → `plan-pending-created`

| Câmp | Conținut |
|---|---|
| **Subiect** | Anunț de job publicat |

**Mesaj:**
> Am publicat anunțul tău de job în pachetul selectat. Factura finală va fi trimisă prin e-mail, de obicei în termen de 1 zi, după procesarea cu succes a plății cu cardul.

---

### 3.2 Plată cu cardul reușită
**Sursă:** `dj/lang/ro/mail.php` → `plan-pending-success`

| Câmp | Conținut |
|---|---|
| **Subiect** | Plată cu card reușită |

**Mesaj:**
> Plata cu cardul a fost reușită. Îți trimitem factura atașată.

---

### 3.3 Plată cu cardul refuzată
**Sursă:** `dj/lang/ro/mail.php` → `plan-pending-failed`

| Câmp | Conținut |
|---|---|
| **Subiect** | Plată cu cardul refuzată |

**Mesaj:**
> Debitarea cardului bancar a eșuat, furnizorul a refuzat plata cu cardul. Anunțul tău a fost mutat în pachetul fără cofeină.

---

### 3.4 Pachet de anunțuri expiră în curând
**Sursă:** `dj/lang/ro/mail.php` → `job-expires`

| Câmp | Conținut |
|---|---|
| **Subiect** | Pachetul tău de anunțuri expiră în o săptămână |

**Mesaj:**
> Pachetul asociat cu jobul următor expiră în 1 săptămână: **:job @ :company**.
>
> În prezent, jobul rulează în pachetul **:plan** până la data **:date**.

**CTA:** Uită-te la candidați și dă-le feedback!

---

### 3.5 Pachet de anunțuri expirat
**Sursă:** `dj/lang/ro/mail.php` → `job-expired`

| Câmp | Conținut |
|---|---|
| **Subiect** | Pachetul tău de anunțuri a expirat |

**Mesaj:**
> Pachetul **:plan** pentru jobul următor a expirat: **:job @ :company**.
>
> Jobul tău va fi închis automat. Vei putea oricând vizualiza candidaturile. Jobul închis poate fi republicat oricând.

**CTA-uri:**
- Dacă mai cauți colegul ideal, alege un nou pachet pentru job!
- Dacă l-ai găsit, închide jobul!

---

### 3.6 Job închis automat
**Sursă:** `dj/lang/ro/mail.php` → `job-autoclose`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ți-am închis jobul |

**Mesaj:**
> Cu două săptămâni în urmă, pachetul **:plan** pentru jobul următor a expirat: **:job @ :company**.
>
> După aceea, jobul tău a fost vizibil pe site-ul DreamJobs încă 2 săptămâni, dar astăzi l-am închis automat.

**CTA:** Dacă dorești să mai publici jobul, apasă aici:

---

### 3.7 Job închis (notificare B2B)
**Sursă:** `dj/lang/ro/mail.php` → `closedjob`

| Câmp | Conținut |
|---|---|
| **Subiect** | Anunț inchis |

**Mesaj:**
> Salut, jobul tău :jobname s-a încheiat.
>
> Notifică-ți candidații despre stadiul actual al recrutării cu un mesaj automat pe pagina Gestionare job închis.
>
> Te rugăm să ne oferi feedback dacă ai găsit candidatul potrivit!

---

### 3.8 Job închis — notificare candidați
**Sursă:** `dj/lang/ro/mail.php` → `closed-job-page.mail-text`

| Câmp | Conținut |
|---|---|
| **Subiect** | *(definit în șablon)* |

**Mesaj:**
> Dragă Candidat,
>
> Anterior ai candidat la poziția **:job @ :company**.
>
> Anunțul de job s-a închis. Dacă ești considerat potrivit pentru poziție, vei fi contactat în curând.
>
> Între timp, uită-te la ofertele noastre actuale de joburi! »

---

### 3.9 Ofertă upgrade pachet de job
**Sursă:** `dj/lang/ro/mail.php` → `job-plan-upgrade`

| Câmp | Conținut |
|---|---|
| **Subiect** | Raport periodic DreamJobs :job - Opțiune upgrade |

**Mesaj:**
> Vă informăm că, conform recomandărilor noastre, **acest tip și nivel de seniority al jobului este cel mai bine publicat în pachetul următor:** :plans
>
> Mai multe informații despre pachetele de publicare: LISTA DE PREȚURI

**Opțiuni:**
> **UPGRADE:** Cumpărați un anunț mai mare! Opriți **în 7 zile**, duplicați, republicați în pachetul mai mare! Veți primi valoarea anunțului oprit sub formă de cupon de reducere.
>
> **REPUBLICARE DUPĂ EXPIRARE:** Cumpărați un anunț mai mare **ACUM**, utilizați-l în decurs de 6 luni!

**Pachete recomandate:**
> - **Espresso:** 3.500 - 5.000 reach (pentru joburi de nivel entry, junior general)
> - **Latte:** 20.000 - 30.000 reach (IT Junior, alte joburi nivel Medior)
> - **Cappuccino:** 50.000 - 70.000 reach (IT Medior și Senior, alte joburi Senior)
> - **Cappuccino Extra:** 100.000 - 140.000 reach (pentru poziții IT dificile, căutare continuă)

**CTA:** CUMPĂRARE ANUNȚ NOU CU REDUCERE  
**Mulțumire:** Vă mulțumim că publicați pe DreamJobs!

---

### 3.10 Factură nouă
**Sursă:** `dj/lang/ro/mail.php` → `new-invoice`

| Câmp | Conținut |
|---|---|
| **Subiect** | Factură nouă |

**Mesaj:**
> Ai primit o factură nouă.

**Notă:** Factura o găsești și atașată la e-mail.  
**CTA:** Poți vizualiza facturile tale aici — Facturi companie

---

### 3.11 Factură proformă nouă
**Sursă:** `dj/lang/ro/mail.php` → `new-proforma-invoice`

| Câmp | Conținut |
|---|---|
| **Subiect** | Factură proformă nouă |

**Mesaj:**
> Ai primit o factură proformă nouă. Achit-o cât mai curând, pentru a putea începe să căutăm noul tău coleg ideal!

**Notă:** Factura proformă o găsești și atașată la e-mail.

---

### 3.12 Factură proformă expiră în curând
**Sursă:** `dj/lang/ro/mail.php` → `payment-expires`

| Câmp | Conținut |
|---|---|
| **Subiect** | Termenul de plată pentru factura proformă va expira în curând |

**Mesaj:**
> Atenție, termenul de plată al uneia dintre facturile tale proforma expiră în 3 zile.

**Notă:**
> Factura proformă o găsești atașată.
>
> După ce suma va fi achitată, te vom anunța și anunțul tău va deveni activ pe DreamJobs Romania.

---

### 3.13 Factură proformă expirată
**Sursă:** `dj/lang/ro/mail.php` → `payment-expired`

| Câmp | Conținut |
|---|---|
| **Subiect** | Factura proformă a expirat |

**Mesaj:**
> Din păcate, termenul de plată al uneia dintre facturile tale proforma a expirat.

**Informație:**
> Această factură proformă nu mai poate fi plătită.
>
> Dacă a apărut o eroare și ai plătit deja factura proformă, te rugăm să ne contactezi la: :email

---

### 3.14 Pachet achiziționat disponibil
**Sursă:** `dj/lang/ro/mail.php` → `payment-settled`

| Câmp | Conținut |
|---|---|
| **Subiect** | Pachetele achiziționate sunt acum disponibile. |

**Mesaj:**
> Ai achiziționat cu succes pachetul/pachetele - :packages! Acesta este acum disponibil pe profilul tău până la data :date.
>
> Pentru a le utiliza, conectează-te la profilul tău, deschide anunțul pe care dorești să îl activezi și, sub pachetele disponibile, selectează pachetul/pachetele pe care dorești să le folosești făcând clic pe "folosește".

---

### 3.15 Cupon PPC utilizat
**Sursă:** `dj/lang/ro/mail.php` → `used-pp-coupon`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ai cumpărat cu succes 1 buc. anunț :coupon |

**Mesaj:**
> La :date, ai cumpărat cu succes 1 buc. anunț **:coupon** pentru jobul următor:

**Info suplimentar:**
- Numărul de anunțuri suplimentare disponibile:
- Cupoanele tale de reducere:
- **CTA:** Clic AICI pentru a cumpăra alte anunțuri!

---

### 3.16 Cupon expiră în curând
**Sursă:** `dj/lang/ro/mail.php` → `coupon-expire`

| Câmp | Conținut |
|---|---|
| **Subiect** | Te-ai uitat de reducere? |

**Mesaj:**
> Cuponul tău este trist... te-ai uitat de el? :(
>
> Cuponul tău este valabil doar până mâine la miezul nopții (:date). Nu rata reducerea!

**Promo:**
> NU AI O POZIȚIE DESCHISĂ ACUM?
>
> Plătește mai puțin acum și folosește anunțul în următoarele 6 luni, când este actual!

**CTA:** Apasă aici pentru a cumpăra

---

## 4. Gestionarea Companiei

### 4.1 Companie înregistrată
**Sursă:** `dj/lang/ro/mail.php` → `company-registered`  
**Șablon:** `mail.company-registered`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe DreamJobs! |

**Mesaj (piața RO):**
> Salut!
>
> Te-ai înregistrat cu succes și ești cu un pas mai aproape de a găsi cei mai potriviți candidați.
>
> 👉 Ca prim pas, creează și publică profilul companiei tale...
>
> Îți mulțumim că ai ales DreamJobs!

---

### 4.2 Invitație editor companie (utilizator existent)
**Sursă:** `dj/lang/ro/mail.php` → `manager-added`

| Câmp | Conținut |
|---|---|
| **Subiect** | Invitație ca editor al companiei |

**Mesaj:**
> **:name** te-a invitat ca editor al companiei **:company**.
>
> Apasă aici pentru a accepta invitația și să înceapă distracția!

---

### 4.3 Activare cont (manager nou creat)
**Sursă:** `dj/lang/ro/mail.php` → `added-manager`  
**Șablon:** `mail.activateaddedaccount`

| Câmp | Conținut |
|---|---|
| **Subiect** | Invitație ca editor al companiei: :company |

**Mesaj:**
> :name te-a invitat ca editor la compania **:company**.
>
> Apasă aici pentru a activa profilul tău și să înceapă distracția!

---

### 4.4 Drepturi de editor revocate
**Sursă:** `dj/lang/ro/mail.php` → `manager-remove`

| Câmp | Conținut |
|---|---|
| **Subiect** | Nu mai ești editorul companiei :company |

**Mesaj:**
> Am crezut că ar trebui să știi: de acum înainte nu mai ești editorul companiei **:company**.
>
> Profilul tău de pe DreamJobs va fi accesibil în continuare:

---

### 4.5 Profil editor activat
**Sursă:** `dj/lang/ro/mail.php` → `manager-activated`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ți-am activat profilul de editor |

**Mesaj:**
> Ți-ai activat cu succes profilul de editor.
>
> Poți începe deja să editezi profilul companiei și să publici anunțuri de joburi!

**Ghid:** Am publicat un ghid în care am rezumat de ce vei avea nevoie pentru a-ți compune profilul de companie.  
**CTA:** Ghid: Structura profilului de companie  
**Dashboard:** Descoperă panoul de control — acesta este sufletul tuturor!  
**Urare:** Spor la treabă, sperăm că veți găsi curând noul vostru coleg grozav!

---

### 4.6 Email de bun venit manager (standard)
**Sursă:** `dj/lang/ro/mail.php` → `manager-welcome`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe DreamJobs! |

**Mesaj:**
> Ți-ai înregistrat cu succes contul de editor.
>
> Poți începe deja să editezi profilul companiei și să publici anunțuri de joburi!

---

### 4.7 Email de bun venit manager (campanie SZMD)
**Sursă:** `dj/lang/ro/mail.php` → `manager-welcome-szmd`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bine ai venit pe DreamJobs - căutăm Locuri de muncă iubibile din România! 🤍 |

**Mesaj:**
> Ne bucurăm că ești alături de noi! Ți-ai înregistrat cu succes contul de editor pe DreamJobs!
>
> **Care este pasul următor?**
> 1. **Creează-ți profilul de companie**: Folosește diferite servicii prin intermediul panoului de control.
> 2. **Publică primul tău anunț**: Profitați de avantajele și serviciile DreamJobs.
> 3. **Bucurați-vă de avantajele DreamJobs**
>
> Ca nou înregistrat, dorim să te surprindem cu **un cupon de 50% reducere unic**, pentru a valorifica la maximum primul tău anunț!
>
> Cuponul de reducere poate fi utilizat pentru pachetele noastre de anunțuri **Espresso, Latte, Cappuccino și Cappuccino Extra** în termen de **o lună**.
>
> **Locuri de Muncă Iubibile :szmd_year: Misiunea noastră pentru un viitor mai bun**
>
> Cu profilul tău de companie publicat, te poți înregistra gratuit la concursul nostru Locuri de Muncă Iubibile...

---

### 4.8 Oportunitate articol blog companie
**Sursă:** `dj/lang/ro/mail.php` → `company-blog-post`

| Câmp | Conținut |
|---|---|
| **Subiect** | DreamJobs oportunitate de articol joburi de vis :job |

**Introducere:**
> Îți mulțumim că publici la noi! Referitor la opțiunea articol de blog inclusă în anunțul :coupon pe care tocmai l-ai lansat, te contactăm în legătură cu următorul anunț de job:

**Mesaj:**
> Pentru a obține un număr eficient de candidați, este recomandat să valorifici oportunitatea oferită de rubrica DreamJobs Joburi de Vis. Experiența arată că articolul de blog crește numărul de candidați cu o medie de **10-15%** în plus...

---

### 4.9 Confirmare ștergere profil
**Sursă:** `dj/lang/ro/mail.php` → `profile-delete` | `dj-api/lang/ro/mail.php` → `profile-delete`

| Câmp | Conținut |
|---|---|
| **Subiect (dj)** | Ștergerea datelor din sistemul DreamJobs Romania |
| **Subiect (dj-api)** | Ștergerea datelor utilizatorului din sistemul DreamJobs! |

**Mesaj (dj):**
> Procesul de ștergere a datelor pentru utilizatorul cu adresa de email :email a fost inițiat la cererea ta.
>
> Procesul complet poate dura până la 30 de zile.
>
> În această perioadă, datele și înregistrările asociate utilizatorului vor fi eliminate din DreamJobs și din sistemele sale conexe.

**Mesaj (dj-api):**
> Procesul de ștergere a datelor asociate contului cu adresa de e-mail :email din sistemul DreamJobs a fost inițiat conform solicitării tale. Pe durata acestui proces, datele și înregistrările corespunzătoare vor fi eliminate din DreamJobs.

---

## 5. Engagement Utilizatori și Marketing

### 5.1 Recomandări de joburi (zilnic)
**Sursă:** `dj/lang/ro/mail.php` → `recommended-jobs`

| Câmp | Conținut |
|---|---|
| **Subiect** | joburi noi pentru tine |

**Mesaj:**
> Bună dimineața! O nouă zi, o nouă oportunitate!
>
> Pe baza categoriilor marcate, credem că următoarele joburi pot fi de interes pentru tine

**Notă:** Modifică categoriile de interese AICI.

---

### 5.2 Recomandări de joburi (săptămânal)
**Sursă:** `dj/lang/ro/mail.php` → `recommended-jobs-weekly`

| Câmp | Conținut |
|---|---|
| **Subiect** | Vrei să-ți dezvolți abilitățile la un job nou? |

**Mesaj:**
> Săptămâna aceasta îți aduce noi oportunități!
>
> Pe baza categoriilor marcate pe profilul tău, credem că următoarele joburi pot fi interesante pentru tine:

---

### 5.3 Memento job salvat
**Sursă:** `dj/lang/ro/mail.php` → `saved-job-reminder`

| Câmp | Conținut |
|---|---|
| **Subiect** | Încă poți aplica! |

**Mesaj:**
> Anterior ai salvat cu succes job-ul de mai jos:

**Avertisment:** Termenul de înregistrare expiră curând. Nu rata jobul tău de vis, aplică chiar azi!

---

### 5.4 Job salvat (notificare)
**Sursă:** `dj/lang/ro/mail.php` → `saved-job`

| Câmp | Conținut |
|---|---|
| **Subiect** | *(valoare HU: Mentett állás — necesită traducere RO)* |

**Mesaj:**
> Mulțumim că ești interesat de poziția deschisă, poți finaliza aplicația ta făcând clic pe următorul link:

---

### 5.5 Newsletter B2B
**Sursă:** `dj/lang/ro/mail.php` → `b2b-newsletter`

| Câmp | Conținut |
|---|---|
| **Subiect** | 🦩 Hai să lansăm vara cu reduceri! ⛱️ |

**Mesaj:**
> În sfârșit vine vara, în sfârșit vacanța și în sfârșit 🌴 **ACȚIUNEA DE VARĂ DREAMJOBS**! 🌊
>
> Intră în profilul companiei tale, caută cuponul **Nyarindito25** în tabloul de bord și folosește-ți reducerea de 25% la pachetele noastre Latte, Cappuccino sau Cappuccino Extra!
>
> Durata promoției: 16-20 iunie 2022.

**CTA:** Spre tabloul de bord!

---

### 5.6 Virtual Bench notificare (confirmare abonare)
**Sursă:** `dj/lang/ro/mail.php` → `virtualbench`

| Câmp | Conținut |
|---|---|
| **Subiect** | Aș lucra aici! |

**Mesaj:**
> Ai lucra aici? Prin abonarea la compania **:company**, vei primi primul notificări despre noile oferte de joburi disponibile aici.
>
> Îți poți gestiona companiile favorite din contul tău personal, la secțiunea de profil.

**Urare:** Vizionare plăcută și îți dorim mult succes în găsirea echipei care te așteaptă!

---

### 5.7 Virtual Bench newsletter (cerere preferințe)
**Sursă:** `dj/lang/ro/mail.php` → `virtualbench-newsletter`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ți-ar plăcea să lucrezi la ei? Completează ce domeniu te interesează! |

**Mesaj:**
> Anterior ai indicat că ți-ar plăcea să lucrezi ca și coleg al companiei **:company**.
>
> Completează sau actualizează-ți profilul cu informațiile despre domeniul și nivelul de poziție care te interesează, pentru a le putea transmite și companiei!

**CTA:** Accesez profilul meu!

---

### 5.8 Virtual Bench newsletter v2
**Sursă:** `dj/lang/ro/mail.php` → `virtualbench-newsletter-2`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ai lucra aici? Ce domeniu te-ar interesa? |

**Mesaj:**
> Ți-ai arătat interesul să lucrezi aici:

**Completare:** Pentru ca firma să îți ofere o oportunitate de muncă relevantă, te rugăm să introduci în profilul tău ce domenii și ce nivel de poziție te-ar interesa!  
**Notă:** *Datele tale personale nu, doar preferințele tale vor fi transmise companiei.

---

### 5.9 Virtual Bench — Notificare job nou
**Sursă:** `dj/lang/ro/mail.php` → `virtualbench-new-job`

| Câmp | Conținut |
|---|---|
| **Subiect** | *(definit în șablon)* |
| **Titlu** | Ai lucra aici? |

**Mesaj:**
> În ultimele săptămâni, luni, te-ai abonat la lista de preferințe a unei companii care ți-a plăcut. Avem vești bune, deoarece compania caută un nou membru pentru echipă.

**Informație:** Nu-ți face griji, datele tale personale vor fi tratate confidențial, aplicația ta va fi vizibilă doar pentru noi, iar alte companii nu vor avea acces la ea! Te poți dezabona oricând sau aici poți edita lista ta de companii la care ai dori să lucrezi!  
**Urare:** O privire plăcută, sperăm că vei găsi cât mai curând jobul visurilor tale!

---

### 5.10 Profil de companie incomplet — memento
**Sursă:** `dj/lang/ro/mail.php` → `unfinished-company-profile`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ai întâmpinat dificultăți în completarea profilului firmei tale? |

**Mesaj:**
> Ai întâmpinat dificultăți în completarea profilului firmei tale? Colegii noștri te ajută cu mare plăcere!
>
> Contactează-ne :contact:
> - E-mail: :email
> - Tel: :phone

---

### 5.11 Vot Lovable Workplaces
**Sursă:** `dj/lang/ro/mail.php` → `lovable-workplaces-voting`

| Câmp | Conținut |
|---|---|
| **Subiect** | ⭐ A început votul Lovable Workplaces! 🚀 |

**Mesaj:**
> Salut! 👋
>
> Compania ta preferată merită să fie cea mai bună! ⭐
> A început votul Lovable Workplaces.
>
> Poți vota foarte simplu:
> 🔎 Caută compania ta preferată în bară de căutare și votează direct de pe pagina ei.
> Sau
> 🎯 Accesează meniu „Votul Lovable Workplaces", unde primești 5 companii aleatorii pentru care poți vota.
>
> Important: Poți vota doar dacă te înregistrezi pe platformă!
>
> 🎁 Cu fiecare vot acordat, îți mărești șansele la premii valoroase.
>
> Intră acum, găsește compania ta preferată și votează!

**Urare:** Mult succes 🚀!

---

### 5.12 Newsletter general
**Sursă:** `dj/lang/ro/mail.php` → `newsletter`

| Câmp | Conținut |
|---|---|
| **Subiect** | Buletin informativ |

**Blocuri de conținut:**
- Aruncă o privire la cele mai recente poziții noastre deschise
- Ți-am selectat și ofertele de joburi evidențiate de pe DreamJobs
- Acestea sunt cele mai noi companii iubibile ale noastre:

**Urare:** Îți dorim să găsești echipa care te așteaptă deja să lucreze cu tine.

---

## 6. DevChallenge

### 6.1 Competiție nouă lansată
**Sursă:** `dj/lang/ro/mail.php` → `dc-new-challenge`

| Câmp | Conținut |
|---|---|
| **Subiect** | Competiția :title a început pe DevChallenge! |

**Mesaj:**
> Nu rata! Competiția **:title** tocmai a început pe DevChallenge! Și în această lună poți câștiga premii valoroase dacă te afli pe podium la sfârșitul concursului!

**CTA:** Mă alătur competiției  
**Link:** Despre ce este competiția?

---

### 6.2 Bun venit (după înregistrare DC)
**Sursă:** `dj/lang/ro/mail.php` → `dc-welcome`

| Câmp | Conținut |
|---|---|
| **Subiect** | Bun venit pe DevChallenge! |

**Mesaj:**
> Felicitări, înregistrarea ta pe DevChallenge a reușit!
>
> Testează-te în mai multe limbaje de programare și încearcă și subiectele amuzante!
>
> Nu uita: poți completa mai multe seturi de întrebări pe categorie și poți chiar să-ți provoci prietenii, ca să nu mai vorbim de premiile valoroase!

**CTA:** Să înceapă completarea chestionarelor!

---

### 6.3 Activitate utilizator (7 zile, activ)
**Sursă:** `dj/lang/ro/mail.php` → `dc-user-active`

| Câmp | Conținut |
|---|---|
| **Subiect (7 zile)** | Te așteaptă mai multe chestionare pe DevChallenge! |
| **Subiect (15 zile)** | Te așteptăm înapoi pe DevChallenge! |
| **Subiect (30 zile)** | Îți mulțumim că ești alături de noi de o lună pe DevChallenge! |

**Mesaj 7 zile:**
> Ne bucurăm că ești deja de o săptămână un membru activ al comunității DevChallenge!
> Și în acest timp nu ai stat degeaba, ai completat deja :total chestionare! Ca relaxare, încearcă și chestionarele noastre amuzante:

**Mesaj 15 zile:**
> De cincisprezece zile ești înregistrat în comunitatea DevChallenge și în acest timp ai completat :total chestionare!
> Activitate fantastică! Pe baza completărilor tale anterioare, îți recomandăm și aceste chestionare:

**Mesaj 30 zile:**
> A trecut deja o lună de când te-ai alăturat comunității DevChallenge! Mulțumiri speciale pentru că în acest timp ai participat activ și la completarea chestionarelor! Ai mai încercat aceste chestionare ale noastre?

---

### 6.4 Activitate utilizator (utilizatori inactivi)
**Sursă:** `dj/lang/ro/mail.php` → `dc-user-inactive`

| Câmp | Conținut |
|---|---|
| **Subiect (7 zile)** | Te așteptăm înapoi pe DevChallenge! |
| **Subiect (15 zile)** | Chestionare interesante te așteaptă pe DevChallenge! |
| **Subiect (15 zile v2)** | E momentul să te testezi cu chestionarele DevChallenge! |
| **Subiect (30 zile)** | Te așteaptă DevChallenge de o lună! |

**Mesaj 7 zile:**
> Îți mulțumim că ești deja de o săptămână membru al comunității DevChallenge. Cu tristețe observăm că în acest timp ai completat doar câteva chestionare. Pe baza completărilor tale anterioare, credem că aceste chestionare te-ar putea interesa:

---

### 6.5 Seria ta este în pericol
**Sursă:** `dj/lang/ro/mail.php` → `dc-user-streak`

| Câmp | Conținut |
|---|---|
| **Subiect** | Seria ta este în pericol! |

**Mesaj:**
> Completează un chestionar pentru ca seria ta să nu se piardă!

**CTA:** Completez un chestionar

---

### 6.6 Rezultate săptămânale
**Sursă:** `dj/lang/ro/mail.php` → `dc-weekly-results`

| Câmp | Conținut |
|---|---|
| **Subiect** | Acesta a fost săptămâna ta pe DevChallenge! |

**Mesaj:**
> Îți mulțumim că ai fost activ pe DevChallenge și săptămâna aceasta! Cu răspunsurile tale la chestionarele noastre, ai obținut următoarele rezultate:

**Format statistici:**
> Cu răspunsurile tale, te afli pe locul **:weekly** în clasamentul săptămânal al categoriei **:category**.
> Locul tău în clasamentul general săptămâna aceasta: **:alltime.**
>
> Ai completat **:quizes** chestionare în categoria **:category**.
> Acuratețea actuală a răspunsurilor tale în categoria **:category**: **:accuracy**

**Motivare:** Vrei rezultate și mai bune? Iată un chestionar cu care poți urca în clasament:  
**Urare:** Îți dorim mult succes și săptămâna viitoare!

---

## 7. Locuri de Muncă Iubibile (SZMD/Lovable Workplaces)

### 7.1 Nominalizare retrasă
**Sursă:** `dj/lang/ro/mail.php` → `szmd-redact`

| Câmp | Conținut |
|---|---|
| **Subiect** | Retrage nominalizarea SZMD:year |

**Mesaj:**
> [:company](:url) și-a retras nominalizarea pentru :year SZMD.

---

### 7.2 Renominalizare
**Sursă:** `dj/lang/ro/mail.php` → `szmd-renominate`

| Câmp | Conținut |
|---|---|
| **Subiect** | Renominalizarea SZMD:year |

**Mesaj:**
> Great news — [:company](:url) has decided to jump back in and renominate for the **Lovable Workplaces Award!**

*(Notă: textul este în engleză în fișierul sursă RO)*

---

### 7.3 Campanie promo Lovable Workplaces (RO ediție)
**Sursă:** `dj/lang/ro/mail.php` → `szmd-promo-ro`

| Câmp | Conținut |
|---|---|
| **Subiect** | Sunteți un loc de muncă lovable? Înregistrați-vă acum! |

**Mesaj:**
> În al treilea an, lansăm competiția Locuri de Muncă Iubibile în :szmd_year! Anul acesta, 30 de companii vor primi Premiul Locuri de Muncă Iubibile, dintre care 3 vor fi selectate de juriu pentru Premiul Special Employer Branding. Înscrierea începe astăzi!

---

### 7.4 Campanie promo Lovable Workplaces (standard)
**Sursă:** `dj/lang/ro/mail.php` → `szmd-promo`

| Câmp | Conținut |
|---|---|
| **Subiect** | Sunteți un loc de muncă lovable? Înregistrați-vă acum! |

**Mesaj:**
> În :szmd_year lansăm concursul Lovable Workplaces pentru al șaselea an consecutiv! Anul acesta 30 de companii vor primi premiul Lovable Workplaces, dintre care 6 vor fi selectate de juriu pentru premiile profesionale speciale în categoriile HR și Employer Branding. Intrarea începe astăzi!
>
> Tema concursului Lovable Workplaces din acest an este: **Creșterea digitalizării în lumea muncii. Arată-ne care sunt soluțiile tale digitale preferate**: adaugă-le la profilul tău!
>
> Rolul soluțiilor digitale a crescut rapid în ultimii ani, în special în lumea muncii...
>
> Ținem pumnii pentru voi, așteptăm să vă vedem printre câștigătorii noștri în :szmd_year!

---

## 8. Smart Bench Profile (SBP)

### 8.1 Profil SBP adăugat în baza de date publică
**Sursă:** `dj/lang/ro/mail.php` → `sbp-b2c`

| Câmp | Conținut |
|---|---|
| **Subiect** | 😱 Acum poți primi direct oferte de joburi! Actualizează-ți profilul! ☝️ 😉 |

**Mesaj:**
> Suntem bucuroși să te informăm că profilul tău de self-branding a fost adăugat în **bazele noastre de date publice, accesibile companiilor**. Astfel, angajatorii pot acum **să te contacteze direct cu ofertele lor de joburi**. Este momentul să îți actualizezi și să faci profilul tău și mai atractiv!

**CTA:** ÎMI ACTUALIZEZ PROFILUL  
**Opțiune dezactivare:** Ha nem szeretnéd, hogy a profilod közvetlenül elérhető legyen a munkáltatók számára, egy kattintással ki tudod kapcsolni ezt a szolgáltatást a fiókodban!
*(Notă: textul de dezactivare este în HU în fișierul sursă RO — necesită corecție)*

---

### 8.2 PDF SBP creat
**Sursă:** `dj/lang/ro/mail.php` → `sbp-pdf`

| Câmp | Conținut |
|---|---|
| **Subiect** | Ai creat un CV unic și inteligent, folosește-l! |

**Mesaj:**
> Felicitări!
>
> Ai finalizat cu succes profilul tău de Self-branding, și astfel ai șanse mai mari să aplici pentru job-ul mult visat.
>
> În plus ți-am trimis versiunea de **PDF a CV-ului tău**, pe care o poți folosi oricând fie pe :site, fie pe un alt portal de locuri de muncă. **Vezi CV-ul tău în atașament!**

**Slogan:** Ieși din mulțime și găsește jobul visurilor tale!  
**CTA:** Nu mai ai altceva de făcut decât să dai click aici și să te prezinți viitorului tău angajator!

---

### 8.3 Profil SBP creat (dj-api)
**Sursă:** `dj-api/lang/ro/mail.php` → `sbp_profile_created`

| Câmp | Conținut |
|---|---|
| **Subiect** | Profilul tău Self-Branding este gata! |

**Mesaj:**
> Bună :name!
>
> Procesatorul nostru de CV-uri bazat pe AI al DreamJobs a creat cu succes profilul tău de Self-Branding.
>
> Dacă simți că ceva nu este corect în profilul tău, îți poți actualiza datele oricând.

**CTA:** Vizualizează-ți profilul

---

### 8.4 Credit gratuit Talent Pool SBP
**Sursă:** `dj/lang/ro/mail.php` → `sbp-search-free-credit`

| Câmp | Conținut |
|---|---|
| **Subiect** | Cadou: Contact Credit |

**Mesaj:**
> Avem vești bune! Dacă utilizezi pachetele achiziționate Cappuccino/Cappuccino Extra până la **:date**, vei primi 2 credite de contact pentru fiecare anunț de angajare Cappuccino și 4 credite de contact pentru Cappuccino Extra, pe care le poți utiliza în DreamJobs Talent Pool.
>
> Ce este Talent Pool-ul?
>
> **Talent Pool Candidate Finder** este un skill de căutare bazat pe abilitățile candidaților. Prin această metodă, pe baza preferințelor tale, poți vedea prezentările candidaților activi și pasivi. Din această bază de date, poți salva pe cei mai potriviți candidați. Iar dacă găsești pe cineva cu o ofertă de muncă, poți accesa datele lui prin valorificarea unui credit de contact.
>
> Creditele de contact vor fi disponibile pe Dashboard, în pachete de 10 și 35 de bucăți.

---

### 8.5 Lansare Talent Pool SBP
**Sursă:** `dj/lang/ro/mail.php` → `sbp-search-lunch`

| Câmp | Conținut |
|---|---|
| **Subiect** | Serviciul al DreamJobs Talent Pool Candidate Finder a început! |

**Mesaj:**
> Serviciul "pick and hire" al DreamJobs **Talent Pool Candidate Finder** a început! Ce înseamnă asta? Este un skill de căutare bazat pe abilitățile candidaților...
>
> Promoție introductivă: **până la 30 aprilie 2022**, vom adăuga **2 credite** de contact la fiecare anunț de job **Cappuccino** și **4 credite** de contact la **Cappuccino Extra**. Creditele pot fi folosite până la expirarea anunțului.

---

## 9. Distribuire și Invitații

### 9.1 Link distribuit pe email (job)
**Sursă:** `dj/lang/ro/mail.php` → `share-job`

| Câmp | Conținut |
|---|---|
| **Subiect** | :from ți-a trimis un link |

**Mesaj:**
> :name ți-a trimis un link către o anunț de job de pe site-ul DreamJobs Romania

**CTA:** Uită-te la anunțul de job

---

### 9.2 Link distribuit pe email (companie)
**Sursă:** `dj/lang/ro/mail.php` → `share-company`

| Câmp | Conținut |
|---|---|
| **Subiect** | :from ți-a trimis un link |

**Mesaj:**
> :name ți-a trimis un link către profilul unei companii de pe site-ul DreamJobs Romania

**CTA:** Uită-te la profilul companiei

---

## 10. Recenzii

### 10.1 Notificare recenzie job
**Sursă:** `dj/lang/ro/mail.php` → `job-review`  
**Șablon:** `mail.jobreviewcreated`

| Câmp | Conținut |
|---|---|
| **Subiect** | Sugestie nouă |

**Mesaj:**
> Am examinat anunțul de job din perspective HR și Marketing și avem următoarele sugestii:

**CTA:** Modific anunțul meu  
**Sugestie:** Te rugăm să modifici anunțul cât mai curând pentru o relevanță mai mare și mai mulți candidați.  
**Mulțumire:** Îți mulțumim că publici la noi!  
**Ajutor:** Dacă ai alte întrebări, nu ezita să contactezi persoana de contact DreamJobs.

---

## 11. Administrare și Altele

### 11.1 Interes profil Gold (solicitantului)
**Sursă:** `dj/lang/ro/mail.php` → `gold-request-b2b`

| Câmp | Conținut |
|---|---|
| **Subiect** | Interes față de profilul GOLD DreamJobs |

**Mesaj:**
> Am primit cu plăcere interesul tău față de serviciul nostru GOLD Profile.
>
> Colegul nostru te va contacta în curând pentru a discuta detaliile și a te ajuta cu comanda.

---

### 11.2 Consiliere în carieră (pentru admin)
**Sursă:** `dj/lang/ro/mail.php` → *(șablon: `mail.admin_asked_for_career_advice`)*

| Câmp | Conținut |
|---|---|
| **Subiect** | Consiliere în carieră: :name |

*(Notificare internă admin — conține numele utilizatorului, e-mail, comentarii și fișiere)*

---

### 11.3 Comandă Candidate Shortlist
**Sursă:** `dj/lang/ro/mail.php` → *(șablon: `mail.candidate_shortlist`)*

| Câmp | Conținut |
|---|---|
| **Subiect** | :name - Comandă Candidate Shortlist |

*(Notificare internă admin)*

---

### 11.4 Recomandare Sourcing
**Sursă:** `dj/lang/ro/mail.php` → `csl-recomendation`

**Mesaj:**
> Anunțul tău de job rulează de 14 zile.
> Dacă nu ești mulțumit de candidați, dorim să îți atragem atenția asupra serviciului nostru de SOURCING, cu ajutorul căruia îți aducem potențiali angajați care sunt deschiși la ofertele voastre.
> În plus, poți primi înapoi prețul pachetului de publicare!

---

### 11.5 Promoție Crăciun/Paști
**Sursă:** `dj/lang/ro/mail.php` → `xmashunt`

| Câmp | Conținut |
|---|---|
| **Subiect** | Acțiunea XMASHUNT! |

**Mesaj (pentru companii):**
> Ai primit un cupon de :discount % reducere ca parte a promoției de Crăciun „XMASHUNT".
>
> Cod cupon: :coupon
>
> Cuponul poate fi folosit pentru următoarele anunțuri: Latte, Cappuccino.

**Urare:** *(nu este specificat în fișierul sursă — se deduce din context: Crăciun fericit!)*

---

### 11.6 Elemente de subsol ale notificărilor

| Element | Text |
|---|---|
| Dezabonare | Dorești să te dezabonezi de la această listă? Poți face asta apăsând aici |
| Adresă poștală | Adresa noastră poștală |
| Salutare | Numai bine / Toate cele bune |
| Intro | Bună / Dragă :name! / Salut :name! |
| Rămas bun | Mult succes! / Cu drag, |
| Semnătură echipă | Echipa DreamJobs / Echipa DreamJobs Romania |
| GDPR | Vă rugăm să tratați datele candidaților primite în acest e-mail cu confidențialitate, în conformitate cu reglementările privind protecția datelor (GDPR). |

---

*Ultima actualizare: 2026-05-26 — Generat pe baza unui audit automatizat al bazei de cod.*
