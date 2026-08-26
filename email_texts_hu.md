# Email Szövegek — Magyar (HU)

> **Platform:** DreamJobs HU  
> **Forrás:** `dj/resources/lang/hu/mail.php` + `dj-api/lang/hu/mail.php`  
> **Utolsó frissítés:** 2026-05-26  
> **Megjegyzés:** A `:placeholder` jelölések dinamikus adatok (pl. `:name`, `:company`, `:job`).  
> A HTML tagek az eredeti forráskódból származnak — az emailek HTML formátumban kerülnek kiküldésre.

---

## Tartalomjegyzék

1. [Regisztráció és Hitelesítés](#1-regisztráció-és-hitelesítés)
2. [Állásjelentkezések](#2-állásjelentkezések)
3. [Állástervek és Számlázás](#3-állástervek-és-számlázás)
4. [Cégkezelés](#4-cégkezelés)
5. [Felhasználói Engagement és Marketing](#5-felhasználói-engagement-és-marketing)
6. [DevChallenge](#6-devchallenge)
7. [SZMD — Szerethető Munkahelyek Díj](#7-szmd--szerethető-munkahelyek-díj)
8. [Smart Bench Profile (SBP)](#8-smart-bench-profile-sbp)
9. [Megosztás és Meghívók](#9-megosztás-és-meghívók)
10. [Értékelések](#10-értékelések)
11. [Adminisztráció és Egyéb](#11-adminisztráció-és-egyéb)

---

## 1. Regisztráció és Hitelesítés

### 1.1 Üdvözlő email (dj — dashboard felhasználó)
**Forrás:** `dj/lang/hu/mail.php` → `welcome`  
**Sablon:** `mail.welcome`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DreamJobs-on! |

**Üzenet:**
> Üdv a jófej álláskeresők közt, mi a DreamJo.bs-nál nagyon örülünk, hogy csatlakoztál!
>
> Reméljük, hamar megtalálod, amit keresel, legyen az rugalmas munkaidő, kutyabarát office, vagy egyszerűen csak magasabb fizetés.
>
> Mutatjuk, hol találod az ország legszerethetőbb állásait:

**Aláírás:** Nagyon szurkolunk, eredményes álláskeresést!

---

### 1.2 Üdvözlő email (dj-api — job seeker regisztráció)
**Forrás:** `dj-api/lang/hu/mail.php` → `welcome`  
**Sablon:** `mail/welcome.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DreamJobs-on! |

**Üzenet:**
> Üdv a DreamJobs-nál, örülünk, hogy itt vagy!
>
> Bízunk benne, hogy hamarosan rátalálsz új álommunkahelyedre - jelentsen ez rugalmas munkaidőt, összetartó csapatot vagy épp szintlépést a karrieredben.
>
> Nézz be a cégek kulisszái mögé, és válassz a hozzád illő pozíciók közül:

**Self-Branding promo blokk:**
> Szeretnénk hatékonyan támogatni az álláskeresésben, ezért készítettük el egyedi álláskeresői megoldásunkat. Self-Branding profiljainkkal kitűnhetsz a többi jelölt közül, és kiemelheted a jelentkezésed - mutasd be kreatív eszköztárunk segítségével, hogy miben vagy erős, mitől vagy különleges!

**CTA:** Megnézem az állásokat | Elkészítem a Self-Branding profilom  
**Üdvözlet:** Sikeres álláskeresést kívánunk a Csapatunk nevében!  
**Segítség:** Ha bármiben segíthetünk, nyugodtan keress minket a hello@dreamjobs.hu címen.

---

### 1.3 Üdvözlő email (dj-api — RO piac, magyar nyelvű változat)
**Forrás:** `dj-api/lang/hu/ro-mail.php` → `welcome`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DreamJobs Romania oldalon! |

**Üzenet:**
> Üdv a jófej álláskeresők közt, mi a DreamJobs-nál nagyon örülünk, hogy csatlakoztál!
>
> Reméljük, hamar megtalálod, amit keresel, legyen az rugalmas munkaidő, kutyabarát office, vagy egyszerűen csak magasabb fizetés.
>
> Mutatjuk, hol találod az ország legszerethetőbb állásait:

**Segítség:** business@dreamjobs.ro  
**Üdvözlet:** Nagyon szurkolunk, eredményes álláskeresést!

---

### 1.4 Email cím megerősítése
**Forrás:** `dj/lang/hu/mail.php` → `email-validation` | `dj-api/lang/hu/mail.php` → `email-validation`  
**Sablon:** `mail.email_validation`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Igazold vissza az e-mail címed |

**Üzenet:**
> Gratulálunk, sikeres regisztráció! Egy teendőd van még, kérünk erősítsd meg email címed az alábbi linkre kattintva:

---

### 1.5 Jelszó-visszaállítás kérés (dj — dashboard)
**Forrás:** `dj/lang/hu/mail.php` → `password-reset.request`  
**Sablon:** `mail.passwordresetrequest`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Elfelejtett jelszó |
| **Cím** | Új jelszó megadása |

**Üzenet:**
> Úgy tűnik, elfelejtetted a DreamJo.bs profilodhoz tartozó jelszavad.
>
> Sebaj, adj meg új jelszót itt:

---

### 1.6 Jelszó megváltoztatva (dj — dashboard)
**Forrás:** `dj/lang/hu/mail.php` → `password-reset.success`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Megváltozott a jelszavad |

**Üzenet:**
> Sikeresen megváltoztattad a jelszavad a DreamJo.bs profilodhoz.

---

### 1.7 Jelszó-visszaállítás (dj-api — job seeker)
**Forrás:** `dj-api/lang/hu/mail.php` → `password-reset`  
**Sablon:** `mail/password-reset.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Jelszó visszaállítása |

**Üzenet:**
> Ezt az e-mailt azért küldük, mert jelszó-visszaállítási kérelmet kezdeményeztél.

**CTA:** Jelszó visszaállítása  
**Tájékoztató:** Ha nem te kérted a jelszó visszaállítását, akkor nincs további teendőd.  
**Figyelmeztetés:** Ez a jelszó-visszaállító link :count perc múlva lejár.

---

### 1.8 OTP (Egyszeri bejelentkezési kód)
**Forrás:** `dj-api/lang/hu/mail.php` → `otp`  
**Sablon:** `mail/otp.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Bejelentkezési kód |

**Üzenet:**
> Az alábbi 6 számjegyű kód segítségével tudsz bejelentkezni a fiókodba:

**Figyelmeztetés:** Ez a kód :count percig érvényes.  
**Tájékoztató:** Ha nem te kérted ezt a kódot, kérjük, hagyd figyelmen kívül ezt az üzenetet.

---

### 1.9 Állásértesítő feliratkozás megerősítése
**Forrás:** `dj-api/lang/hu/mail.php` → `job-notification`  
**Sablon:** `mail/job-notification.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Feliratkoztál a DreamJobs állásértesítőjére |

**Üzenet:**
> Kedves :name!
>
> Sikeresen feliratkoztál az állásértesítő hírlevelünkre, így egy lépéssel közelebb kerültél, hogy rátalálj új munkahelyedre.
>
> Mostantól a megadott érdeklődési körök alapján személyre szabott állásértesítőket küldünk neked, hogy minél gyorsabban rátalálj a következő nagy lehetőségre – legyen az rugalmas munkaidő, inspiráló munkakörnyezet, kutyabarát iroda vagy épp vonzóbb juttatási csomag.
>
> A belépéshez szükséges ideiglenes jelszavad: **:pw**
>
> Ha úgy érzed, túl sok értesítést kapsz, a levelek alján található Leiratkozás gombra kattintva, vagy IDE KATTINTVA könnyedén módosíthatod a beállításaidat.
>
> Kérdés esetén írj bátran a :address címre.
>
> Sikeres álláskeresést kívánunk!

---

## 2. Állásjelentkezések

### 2.1 Sikeres állásjelentkezés (B2C — jelölt visszaigazoló, dj)
**Forrás:** `dj/lang/hu/mail.php` → `applied-to-job`  
**Sablon:** `mail.applied_to_job`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Sikeres állásjelentkezés: :company @ :job |

**Üzenet:**
> Gratulálunk, sikeresen jelentkeztél a **:job** pozícióra a **:company** céghez a DreamJobs álláspotálon.
>
> A cég a jelentkezésed fogadta, türelmedet kérjük! Ha kérdésed lenne, írj nekünk: :email

**Megosztott adatok blokkja:** A következő adataidat osztottuk meg velük, hogy felvehessék veled a kapcsolatot.

**SBP promo:**
> **Tudtad, hogy már Self-branding profillal is jelentkezhetsz az állásokra nálunk? Átlagosan 10 jelentkezésből csak 2 interjú jöhet össze. Növeld az esélyed a kiválasztás során, töltsd ki és jelentkezz könnyedén legközelebb azzal!**

**CTA-k:**  
- Nézz szét azon között a cégek között, akiknél a toborzás nem állt meg!  
- Jelentkezz a többi, hasonló állásunkra is!

**Üdvözlet:** Sikeres álláskeresést!

---

### 2.2 Sikeres állásjelentkezés (B2C — jelölt visszaigazoló, dj-api)
**Forrás:** `dj-api/lang/hu/mail.php` → `application-b2c`  
**Sablon:** `mail/application_b2c.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Sikeres állásjelentkezés: :company @ :job |
| **Tárgy (cég nélkül)** | Sikeres állásjelentkezés: :job |

**Üzenet (standard):**
> Gratulálunk, sikeresen jelentkeztél a **:job** pozícióra a **:company** céghez a DreamJo.bs állásportálon.
>
> A cég a jelentkezésed fogadta, türelmedet kérjük! Ha kérdésed lenne, írj nekünk: :email

**Üzenet (cég nélkül — hide_company):**
> Gratulálunk, sikeresen jelentkeztél a **:job** pozícióra a DreamJo.bs állásportálon.
>
> A cég a jelentkezésed fogadta, türelmedet kérjük!

**Jelszó ajánló (új felhasználónak):**
> Csak egy jelszót kell megadnod és kész is a DreamJobs regisztrációd. Ezt követően könnyedén tudsz állásokra jelentkezni és bármikor megtekintheted korábbi jelentkezéseid.
>
> Jelszó megadásához és DreamJobs regisztrációd befejezéséhez használd az alábbi linket: link

**SBP promo:**
> **Tudtad, hogy már Self-branding profillal is jelentkezhetsz az állásokra nálunk? Átlagosan 10 jelentkezésből csak 2 interjú jöhet össze. Növeld az esélyed a kiválasztás során, töltsd ki és jelentkezz könnyedén legközelebb azzal!**

**CTA-k:** Nézz szét azon között a cégek között, akiknél a toborzás nem állt meg! | Jelentkezz a többi, hasonló állásunkra is!  
**Üdvözlet:** Sikeres álláskeresést!

---

### 2.3 Új jelentkező értesítő (B2B — cégnek, dj-api)
**Forrás:** `dj-api/lang/hu/mail.php` → `application-b2b`  
**Sablon:** `mail/application_b2b.blade.php`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új jelentkező |

**Üzenet:**
> Remek hírünk van, **:name** jelentkezett a **:job** @ **:company** pozíciódra!!
>
> Nézd meg **:name** jelentkezési adatait és CV-jét!

**CTA:** Állás jelentkezői  
**PS:** Kérünk, hogy mindenképp jelezz vissza neki, akkor is, ha nem releváns az állásra! Ez nemcsak neki fontos, a cégednek is - a jó munkáltatói márka része a visszajelzés.  
**GDPR megjegyzés:** Kérünk hogy a levélben kapott jelentkező adatokat bizalmasan, a hatályos adatvédelmi előírásoknak (GDPR) megfelelően kezeld.

---

### 2.4 Visszautasított pályázat értesítő
**Forrás:** `dj/lang/hu/mail.php` → `application-rejected`  
**Sablon:** `mail.application_rejected`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Álláspályázat eredménye: :company @ :job |

**Üzenet:**
> Sajnálattal értesítünk, hogy a(z) **:job** pozícióra a(z) **:company** cégnél benyújtott jelentkezésed nem került kiválasztásra.

**Bátorítás:** Ne add fel! További izgalmas állásajánlataink várnak rád, amelyek talán még jobban illeszkednek a képességeidhez és karriercéljaidhoz.  
**CTA:** Megnézem az állásokat  
**Üdvözlet:** Sok sikert az álláskereséshez!

---

### 2.5 Állásjelentkezés utáni kérdőív
**Forrás:** `dj/lang/hu/mail.php` → `applied-to-job-survey`  
**Sablon:** `mail.applied_to_job_survey`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Kíváncsian várjuk a véleményed az állásjelentkezésről! :job |

**Üzenet:**
> Köszönjük, hogy az oldalunkon keresztül jelentkeztél egy állásra!
>
> Kíváncsian várjuk a véleményed, kérjük töltsd ki ezt a rövid kérdőívet, segítsd a munkánkat!

**CTA:** Kitöltöm

---

### 2.6 Befejezetlen állásjelentkezés emlékeztető
**Forrás:** `dj/lang/hu/mail.php` → `unfinished-job-application`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Folytasd a jelentkezést |

**Üzenet:**
> Kedves :name!
>
> Korábban félbehagytad az állásra jelentkezésed. Ne felejtsd el elküldeni mielőtt lejárna az állás.
>
> :job_name
>
> [LINK]

---

## 3. Állástervek és Számlázás

### 3.1 Állás megjelent (pending fizetés után)
**Forrás:** `dj/lang/hu/mail.php` → `plan-pending-created`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Álláshirdetés publikálva |

**Üzenet:**
> Az álláshirdetésedet publikáltuk a kiválasztott csomagban. A végszámlát a kártya sikeres terhelése után, várhatóan 1 napon belül elküldjük emailben.

---

### 3.2 Kártyás fizetés sikeres
**Forrás:** `dj/lang/hu/mail.php` → `plan-pending-success`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Sikeres bankártyás fizetés |

**Üzenet:**
> A kártyás fizetés sikeres volt. Mellékelve küldjük a számlád.

---

### 3.3 Kártyás fizetés visszautasítva
**Forrás:** `dj/lang/hu/mail.php` → `plan-pending-failed`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Visszautasított kártyás fizetés |

**Üzenet:**
> A bankkártya terhelése sikertelen volt, a szolgáltató elutasította a kártyás fizetést. A hirdetésedet koffeinmentes csomagba tettük át.

---

### 3.4 Hirdetési csomag hamarosan lejár
**Forrás:** `dj/lang/hu/mail.php` → `job-expires`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Egy hét múlva lejár a hirdetési csomagod |

**Üzenet:**
> 1 hét múlva lejár a következő álláshoz tartozó csomagod: **:job @ :company**.
>
> Az állás most a **:plan** csomagban fut egészen **:date**-ig.

**CTA:** Nézd meg a jelentkezőket, és jelezz vissza nekik!

---

### 3.5 Hirdetési csomag lejárt
**Forrás:** `dj/lang/hu/mail.php` → `job-expired`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Lejárt a hirdetési csomagod |

**Üzenet:**
> Lejárt a **:plan** csomagod a következő állásra: **:job @ :company**.
>
> Az állásodat automatikusan lezárjuk. A jelentkezéseket mindig meg tudod majd tekinteni. A lezárt állást bármikor újra publikálhatod.

**CTA-k:**  
- Ha továbbra is keresed az álommunkatársad, válassz új csomagot az álláshoz!  
- Ha megtaláltad az embered, zárd le az állást!

---

### 3.6 Állás automatikusan lezárva
**Forrás:** `dj/lang/hu/mail.php` → `job-autoclose`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Lezártuk az állásod |

**Üzenet:**
> Két héttel ezelőtt lejárt a **:plan** csomagod a következő állásra **:job @ :company**.
>
> Ezután az állásod még 2 hétig látszott a DreamJo.bs oldalán, de ma automatikusan lezártuk az állásod.

**CTA:** Ha szeretnéd tovább hirdetni az állást, kattintsd ide:

---

### 3.7 Állás lezárva (B2B értesítő)
**Forrás:** `dj/lang/hu/mail.php` → `closedjob`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Lezárt hirdetés |

**Üzenet:**
> Hello, :jobname állásod lezárult.
>
> Értesítsd ki a jelentkezőidet a toborzás jelenlegi állásáról automatikus üzenettel a Lezárt állás kezelése oldalon.
>
> Kérjük adj nekünk visszajelzést, hogy sikerült-e megtalálnod a megfelelő jelöltet!

---

### 3.8 Állás lezárva — jelentkezők értesítése
**Forrás:** `dj/lang/hu/mail.php` → `closed-job-page.mail-text`

| Mező | Tartalom |
|---|---|
| **Tárgy** | *(tárgy a sablonban van meghatározva)* |

**Üzenet:**
> Kedves Jelentkező!
>
> Korábban jelentkeztél a(z) **:job @ :company** állásra.
>
> Az álláshirdetés lezárult. Amennyiben alkalmasnak találnak a pozícióra, hamarosan felveszik veled a kapcsolatot.
>
> Addig is nézz szét aktuális állásajánlataink között! »

---

### 3.9 Hirdetési csomag upgrade ajánlat
**Forrás:** `dj/lang/hu/mail.php` → `job-plan-upgrade`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Időszaki DreamJo.bs Job Riport :job - Upgrade opció |

**Üzenet:**
> Tájékoztatunk, hogy ez a típusú és szenioritású állást **ajánlásunk szerint az alábbi csomagban érdemes hirdetni:** :plans
>
> További információk a hirdetési csomagok kapcsán: ÁRLISTA

**Lehetőségek:**
> **UPGRADE:** Vásárolj nagyobb hirdetést! Állítsd le **7 napon belül**, duplikáld, indítsd újra a nagyobb csomagban jelenlegi hirdetésed! Leállított hirdetésed értékét kedvezmény kupon formájában kapod vissza.
>
> **LEJÁRAT UTÁNI ÚJRA HIRDETÉS:** Vásárolj nagyobb hirdetést **még MA**, használd fel 6 hónapon belül!

**Csomagok ajánlás:**
> - **Espresso:** 3.500 - 5.000 reach (Pályakezdő, általános Junior állásokhoz)
> - **Latte:** 20.000 - 30.000 reach (Junior IT, Medior szintű egyéb állásokhoz)
> - **Cappuccino:** 50.000 - 70.000 reach (Medior és Senior IT állások, egyéb Senior állásokhoz)
> - **Cappuccino Extra:** 100.000 - 140.000 reach (nehéz IT pozíciókhoz, folyamatos kereséshez)

**CTA:** ÚJ HIRDETÉS VÁSÁRLÁS KEDVEZMÉNNYEL  
**Köszönet:** Köszönjük, hogy a DreamJo.bs-on hirdetsz!

---

### 3.10 Új számla
**Forrás:** `dj/lang/hu/mail.php` → `new-invoice`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új számla |

**Üzenet:**
> Új számlád érkezett.

**Megjegyzés:** A számlát a levél csatolmányaként is megtalálod.  
**CTA:** A számláidat itt tudod megnézni — Cég számlái

---

### 3.11 Új díjbekérő (proforma számla)
**Forrás:** `dj/lang/hu/mail.php` → `new-proforma-invoice`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új díjbekérő |

**Üzenet:**
> Új díjbekérőd érkezett. Fizesd be minél hamarabb, hogy elkezdhessük megkeresni a tökéletes új munkatársatokat!

**Megjegyzés:** A díjbekérőt a levél csatolmányaként is megtalálod.

---

### 3.12 Díjbekérő hamarosan lejár
**Forrás:** `dj/lang/hu/mail.php` → `payment-expires`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Hamarosan lejár a díjbekérőd |

**Üzenet:**
> Vigyázz, mert 3 nap múlva lejár az egyik díjbekérőd fizetési határideje.

**Megjegyzés:** A díjbekérőt megtalálod csatolva is.
> Amint beérkezett az összeg, értesítünk, és élesedik az állásod a DreamJo.bs-on.

---

### 3.13 Díjbekérő lejárt
**Forrás:** `dj/lang/hu/mail.php` → `payment-expired`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Lejárt a díjbekérőd |

**Üzenet:**
> Sajnos lejárt az egyik díjbekérőd fizetési határideje.

**Megjegyzés:**
> Ezt a díjbekérőt már nem tudod befizetni.
>
> Ha hiba történt, és már befizetted a díjbekérőt, kérlek vedd fel velünk a kapcsolatot: :email

---

### 3.14 Megvásárolt csomag jóváírva
**Forrás:** `dj/lang/hu/mail.php` → `payment-settled`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Megvásárolt csomag jóváírásra került és felhasználható |

**Üzenet:**
> A megvásárolt - :packages - hirdetési csomag jóváírásra került, mostantól felhasználható :date.-ig
>
> Lépj be az oldalra, nyisd meg a hirdetést, amit el szeretnél indítani és a felhasználható csomag(ok) melletti "felhasználás" gombra kattintva indítsd el azt.

---

### 3.15 PPC kupon beváltva
**Forrás:** `dj/lang/hu/mail.php` → `used-pp-coupon`

| Mező | Tartalom |
|---|---|
| **Tárgy** | :coupon hirdetés beváltásra került |

**Üzenet:**
> :date -én 1 db **:coupon hirdetés** beváltásra került az alábbi álláshoz kapcsolódóan:

**Egyéb info:**
- Rendelkezésre álló további hirdetések száma:
- Elérhető kedvezmény kuponjaim:
- **CTA:** További hirdetés vásárláshoz kattints IDE

---

### 3.16 Kupon hamarosan lejár
**Forrás:** `dj/lang/hu/mail.php` → `coupon-expire`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Megfeledkeztél a kedvezményről? |

**Üzenet:**
> A kedvezmény kuponod szomorú... megfeledkeztél róla? :(
>
> Kuponkódod már csak holnap éjfélig érvényes.(:date). Ne maradj le a kedvezményről!

**Promo szöveg:**
> ÉPPEN NINCS NYITOTT POZÍCIÓD?
>
> Fizess most kevesebbet, és használd fel a hirdetést a következő 6 hónapban, amikor aktuális!

**CTA:** Kattints ide a vásárláshoz

---

## 4. Cégkezelés

### 4.1 Cég regisztrálva
**Forrás:** `dj/lang/hu/mail.php` → `company-registered`  
**Sablon:** `mail.company-registered`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DreamJobs-on! |

**Üzenet (HU piac):**
> Üdvözlünk! Sikeresen regisztráltad a cégedet! Ismerd meg a Vezérlőpultot!
>
> - **Kezdd el elkészíteni a cégprofilodat** és publikáld! Ha segítségre van szükséged, nézd át a segédletünket vagy kérdezz a kijelölt kapcsolattartódtól bizalommal!
>   - :contact_name / :contact_phone / :contact_email
> - **Vedd meg az első hirdetésedet!**
> - **Vásárolj hirdetési csomagokat!** Használd ki a mennyiségi kedvezményeket! Hirdetési csomagjaink 6 hónapos beváltási határidővel használhatók fel!
> - **Készítsd el az ÁLLÁSHIRDETÉSEDET!** Az elkészült álláshirdetéshez válaszd ki az előre megvásárolt hirdetési csomagot és publikáld!
> - Nézd meg a DreamJo.bs egyéb szolgáltatásait is a Dashboardon!
>   - **Gold Business Profil** — Employer Branding szolgáltatás
>   - **Talent Pool** — Jelöltkereső szolgáltatás
>
> Örülünk, hogy Ti is velünk vagytok!

**Üzenet (RO piac):**
> Szia!
>
> Sikeresen regisztráltad a cégedet, és egy lépéssel közelebb kerültél ahhoz, hogy megtaláld a legmegfelelőbb jelölteket.
>
> 👉 Első lépésként hozd létre és publikáld a céges profilodat...
>
> Köszönjük, hogy a DreamJobsot választottad!

---

### 4.2 Meghívás céges szerkesztőnek (meglévő felhasználó)
**Forrás:** `dj/lang/hu/mail.php` → `manager-added`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Meghívás céges szerkesztőnek |

**Üzenet:**
> **:name** meghívott a(z) **:company** céges szerkesztőjének.
>
> Kattints ide, hogy elfogadd a meghívást, és kezdődhet a buli!

---

### 4.3 Fiók aktiválása (új manager létrehozva)
**Forrás:** `dj/lang/hu/mail.php` → `added-manager`  
**Sablon:** `mail.activateaddedaccount`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Meghívás céges szerkesztőnek: :company |

**Üzenet:**
> :name meghívott szerkesztőnek a(z) **:company** céghez.
>
> Kattints ide, hogy aktiváld a profilod, és kezdődhet a buli!

---

### 4.4 Szerkesztői jogosultság elvonva
**Forrás:** `dj/lang/hu/mail.php` → `manager-remove`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Többé nem vagy a :company szerkesztője |

**Üzenet:**
> Gondoltuk, szólunk: mostantól kezdve nem vagy a **:company** szerkesztője.
>
> A DreamJo.bs-os profilodat ezentúl is fogod tudni használni:

---

### 4.5 Szerkesztői profil aktiválva
**Forrás:** `dj/lang/hu/mail.php` → `manager-activated`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Aktiváltuk a szerkesztői profilod |

**Üzenet:**
> Sikeresen aktiváltad a szerkesztői profilodat.
>
> Már el is kezdhetsz céges profilt szerkeszteni és álláshirdetést feladni!

**Segédlet:** Elérhetővé tettünk egy segédlet, amiben összeszedtük, mire lesz szükséged a céges profilod megkomponálásához.  
**CTA:** Segédlet: A céges profil felépítése  
**Dashboard info:** Ismerd meg a vezérlőpultot - ez a lelke mindennek!  
**Üdvözlet:** Hajrá, reméljük, hamar megtaláljátok a jófej új kollégátokat!

---

### 4.6 Manager üdvözlő email (standard)
**Forrás:** `dj/lang/hu/mail.php` → `manager-welcome`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DreamJobs-on! |

**Üzenet:**
> Sikeresen regisztráltad a szerkesztői fiókodat.
>
> Már el is kezdhetsz céges profilt szerkeszteni és álláshirdetést feladni!

---

### 4.7 Manager üdvözlő email (SZMD kampányban)
**Forrás:** `dj/lang/hu/mail.php` → `manager-welcome-szmd`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a Dreamjobson - keressük Magyarország Szerethető Munkahelyeit!🤍 |

**Üzenet:**
> Örülünk hogy itt vagy! Sikeresen regisztráltad szerkesztői fiókodát a Dreamjobs-hoz!
>
> **Mi a következő lépés?**
> 1. **Hozd létre céges profilod**: Használj különböző szolgáltatásokat a Dashboardon keresztül.
> 2. **Tedd közzé első hirdetésed**: Élj a DreamJobs előnyeivel és szolgáltatásaival.
> 3. **Élvezd a DreamJobs nyújtotta előnyöket**
>
> Új regisztrálóként szeretnénk **egy egyszeri 50%-os kedvezménykuponnal** meglepni, hogy a lehető legjobban kihasználhasd az első hirdetésed értékét!
>
> Kedvezményes kuponod az **Espresso, Latte, Cappuccino és Cappuccino Extra** hirdetési csomagjainkra is felhasználhatod **egy hónapon** belül.
>
> **Szerethető Munkahelyek Díj 2024: Mi így teszünk egy jobb világért**
>
> Publikált céges profiloddal ingyenesen nevezhetsz a Szerethető Munkahelyek versenyünkre...

---

### 4.8 Cégblogcikk lehetőség értesítő
**Forrás:** `dj/lang/hu/mail.php` → `company-blog-post`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Álomállások blogcikk lehetőség :job |

**Bevezetés:**
> Köszönjük, hogy nálunk hirdetsz! A most indított :coupon hirdetésben foglalt blog-cikk opció kapcsán keresünk az alábbi álláshirdetésed kapcsán:

**Üzenet:**
> A hatékony jelentkező számhoz érdemes kihasználni a DreamJobs blog Álommelók rovata adta lehetőséget. A tapasztalatok szerint a blogcikk által átlag plusz **10-15%-al nő a jelentkezők száma**...
>
> Mit kell tenned? Mellékeltünk egy rövid KÉRDÉSSORT. Töltesd ki a meghirdetett pozícióhoz hasonló munkakörben lévő kollégával...
>
> Amennyiben szeretnétek élni a blogcikk megjelenés lehetőségével, küldjétek el a válaszaitokat az általatok relevánsnak tartott kérdésekre **7 napon belül**...

---

### 4.9 Profil törlése megerősítő
**Forrás:** `dj/lang/hu/mail.php` → `profile-delete` | `dj-api/lang/hu/mail.php` → `profile-delete`

| Mező | Tartalom |
|---|---|
| **Tárgy (dj)** | Adattörlés DreamJo.bs rendszerből |
| **Tárgy (dj-api)** | Felhasználói adattörlés a DreamJobs rendszerből! |

**Üzenet (dj):**
> Rendszerünkből a(z) :email e-mail címmel regisztrált felhasználóhoz tartozó adatok törlésének folyamata kérésedre megkezdődött.
>
> A teljes folyamat maximum 30 napot vesz igénybe.
>
> Ennek során a felhasználóhoz tartozó adatokat és bejegyzéseket eltávolítjuk a DreamJo.bs-ból és a kapcsolódó rendszerekből.

**Üzenet (dj-api):**
> Rendszerünkből a(z) :email e-mail címmel regisztrált felhasználóhoz tartozó adatok törlésének folyamata kérésedre megkezdődött. Ennek során a felhasználóhoz tartozó adatokat és bejegyzéseket eltávolítjuk a DreamJobs rendszeréből.

---

## 5. Felhasználói Engagement és Marketing

### 5.1 Állásajánlások (napi)
**Forrás:** `dj/lang/hu/mail.php` → `recommended-jobs`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új állások neked |

**Üzenet:**
> Új nap, új lehetőség!
>
> A megjelölt kategóriák alapján az alábbi új állás(ok) érdekes lehet számodra

**Megjegyzés:** Érdeklődési kategóriáidat ITT tudod pontosítani

---

### 5.2 Állásajánlások (heti)
**Forrás:** `dj/lang/hu/mail.php` → `recommended-jobs-weekly`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új munkahelyen fejlesztenéd a tudásod? |

**Üzenet:**
> Ezen a héten is új lehetőségek várnak!
>
> A megjelölt kategóriák alapján az alábbi új állás(ok) érdekes lehet számodra

---

### 5.3 Elmentett állás emlékeztető
**Forrás:** `dj/lang/hu/mail.php` → `saved-job-reminder`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Most még tudsz jelentkezni |

**Üzenet:**
> Korábban sikeresen elmentetted a következő állást:

**Figyelmeztetés:** A jelentkezési határidő hamarosan lejár. Ne maradj le az álom állásodról, jelentkezz még ma!

---

### 5.4 Elmentett állás (értesítő)
**Forrás:** `dj/lang/hu/mail.php` → `saved-job`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Mentett állás |

**Üzenet:**
> Köszönjük, hogy érdeklődsz a nyitott pozíció iránt, a következő linkre kattintva fejezheted be a jelentkezésed:

---

### 5.5 B2B hírlevél
**Forrás:** `dj/lang/hu/mail.php` → `b2b-newsletter`

| Mező | Tartalom |
|---|---|
| **Tárgy** | 🦩 Induljon a nyár akciósan! ⛱️ |

**Üzenet:**
> Végre itt a nyár, végre vakáció és végre 🌴 **DREAMJOBS NYÁRINDÍTÓ AKCIÓ**! 🌊
>
> Lépj be céges profilodra, keresd a dashboardon a **Nyarindito25** kupont és használd fel a 25%-os kedvezményedet Latte, Cappuccino vagy Cappuccino Extra csomagjainkra!
>
> Az akció időtartama: 2022. június 16-20.

**CTA:** Irány a dashboard!

---

### 5.6 Virtual Bench értesítő (feliratkozás visszaigazolás)
**Forrás:** `dj/lang/hu/mail.php` → `virtualbench`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Dolgoznék itt! |

**Üzenet:**
> Dolgoznál itt? A **:company** céghez való feliratkozással mostantól elsőként kapsz értesítést az itt megnyíló állásajánlatokról.
>
> A kedvelt cégeidet a személyes fiókodban, a profil menüpont alatt tudod menedzselni.

**Üdvözlet:** Jó nézelődést és drukkolunk, hogy megtaláld az a csapatot, akik már várnak Rád!

---

### 5.7 Virtual Bench hírlevél (preferenciák kérése)
**Forrás:** `dj/lang/hu/mail.php` → `virtualbench-newsletter`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Szívesen dolgoznál náluk? Add meg, hogy milyen terület érdekel! |

**Üzenet:**
> Korábban jelezted, hogy szívesen dolgoznál a(z) **:company** munkatársaként.
>
> Add meg, vagy aktualizáld profilodban, hogy milyen területen, milyen szintű pozíció érdekelne, hogy tudathassuk a céggel is!

**CTA:** Ugrás a profilomra!

---

### 5.8 Virtual Bench hírlevél v2
**Forrás:** `dj/lang/hu/mail.php` → `virtualbench-newsletter-2`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Dolgoznál itt? Milyen terület érdekelne? |

**Üzenet:**
> Korábban jelezted, hogy szívesen dolgoznál itt:

**Kiegészítés:** Ahhoz, hogy releváns állás lehetőséget kínáljon a cég számodra is, kérjük pár kattintással add meg a profilodon, hogy milyen területen, milyen szintű pozíció érdekelne!  
**Megjegyzés:** *A cég számára a személyes adataid nem, kizárólag a megadott preferenciáid kerülnek átadásra.

---

### 5.9 Virtual Bench — Új állás értesítő
**Forrás:** `dj/lang/hu/mail.php` → `virtualbench-new-job`

| Mező | Tartalom |
|---|---|
| **Tárgy** | *(sablon határozza meg)* |
| **Cím** | "Dolgoznál itt"? |

**Üzenet:**
> Az elmúlt hetekben, hónapokban feliratkoztál egy általad kedvelt cég Dolgoznék itt virtuális kispadjára. Jó hírünk van, mivel a cég új csapattagot keres.

**Tájékoztató:** Ne aggódj, személyes adataidat bizalmasan kezeljük, a jelentkezésed csak mi látjuk, más cég nem fér hozzá! Bármikor leiratkozhatsz, vagy itt tudod szerkeszteni a Dolgoznék itt listád!  
**Üdvözlet:** Jó nézelődést, reméljük, hogy mihamarabb megtalálod az álom állásod!

---

### 5.10 Befejezetlen profil emlékeztető
**Forrás:** `dj/lang/hu/mail.php` → `unfinished-company-profile`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Elakadtál a cégprofil szerkesztéssel? |

**Üzenet:**
> Elakadtál a cégprofil szerkesztéssel? Kapcsolattartóink szívesen segítenek - legyen szó a szolgáltatásainkról, vagy a cégprofil kreatív kitöltéséről.
>
> Keresd :contact:
> - E-mail: :email
> - Tel: :phone

**Promo:** Legyetek ti is a Szerethető Cégek közösségének tagja és mutassátok be magatokat :country első és egyedülálló employer branding platformján!

---

### 5.11 Lovable Workplaces szavazás
**Forrás:** `dj/lang/hu/mail.php` → `lovable-workplaces-voting`

| Mező | Tartalom |
|---|---|
| **Tárgy** | ⭐ Elindult a Lovable Workplaces szavazás! 🚀 |

**Üzenet:**
> Szia! 👋
>
> A kedvenc céged megérdemli, hogy a legjobb legyen! ⭐
> Elindult a Lovable Workplaces szavazás.
>
> Nagyon egyszerűen szavazhatsz:
> 🔎 Keresd meg a kedvenc cégedet a keresőben és szavazz rá közvetlenül az oldaláról.
> Vagy
> 🎯 Lépj be a „Lovable Workplaces szavazás" menüpontba, ahol 5 véletlenszerű céget kapsz, amire szavazhatsz.
>
> Fontos: Csak akkor szavazhatsz, ha regisztrálsz a platformon!
>
> 🎁 Minden leadott szavazattal növeled az esélyed az értékes nyereményekre.
>
> Lépj be most, keresd meg a kedvenc cégedet és szavazz!

**Üdvözlet:** Sok sikert 🚀!

---

### 5.12 Általános hírlevél
**Forrás:** `dj/lang/hu/mail.php` → `newsletter`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Hírlevél |

**Tartalom blokkok:**
- Nézz szét a legfrissebb nyitott pozícióink között
- Kigyűjtöttük Neked a DreamJo.bs kiemelt állásajánlatait is
- Ők pedig a legújabb szerethető cégeink:

**Üdvözlet:** Drukkolunk, hogy megtaláld azt a csapatot, akik már várják, hogy veled dolgozhassanak.

---

## 6. DevChallenge

### 6.1 Új bajnokság indult
**Forrás:** `dj/lang/hu/mail.php` → `dc-new-challenge`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Indul a :title bajnokság a DevChallenge-en! |

**Üzenet:**
> Le ne maradj! Most indul a **:title bajnokság** a DevChallenge oldalán! Ebben a hónapban is értékes nyereményeket szerezhetsz, ha a dobogón találod magad a verseny végén!

**CTA:** Csatlakozom a bajnoksághoz  
**Link:** Hogy miről szól a bajnokság?

---

### 6.2 Üdvözlő (DC regisztráció után)
**Forrás:** `dj/lang/hu/mail.php` → `dc-welcome`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Üdv a DevChallengen! |

**Üzenet:**
> Gratulálunk, a regisztrációd sikeres volt a DevChallenge-re!
>
> Tedd próbára magad több programnyelvben és próbáld ki a szórakoztató témaköröket is!
>
> Ne feledd: témánként több kérdéssort is kitölthetsz és akár a barátaidat is kihívhatod, nem beszélve az értékes nyereményekről!

**CTA:** Indulhat a kvízkitöltés!

---

### 6.3 Felhasználói aktivitás (7 napos, aktív)
**Forrás:** `dj/lang/hu/mail.php` → `dc-user-active`

| Mező | Tartalom |
|---|---|
| **Tárgy (7 nap)** | Újabb kvízek várnak a DevChallenge oldalán! |
| **Tárgy (15 nap)** | Visszavárunk a DevChallenge-be! |
| **Tárgy (30 nap)** | Köszönjük, hogy már egy hónapja velünk vagy a DevChallenge-ben! |

**7 napos üzenet:**
> Örülünk hogy már egy hete aktív tagja vagy a DevChallenge közösségnek!
> És ezidő alatt nem is tétlenkedtél, :total kvízt kitöltöttél már! Kikapcsolódásként próbáld ki szórakoztató kvízeinket is:

**15 napos üzenet:**
> Már tizenöt napja regisztráltál a DevChallenge közösségébe és ezidő alatt :total kvízt töltöttél ki!
> Fantasztikus aktivitás! Az eddigi kitöltéseid alapján javasoljuk neked az alábbi kvízeket is:

**30 napos üzenet:**
> Már egy hónap eltelt, mióta csatlakoztál a DevChallenge közösséghez! Külön köszönet azért, hogy ezidő alatt aktívan részt vettél a kvízek kitöltésében is! Ezeket a kvízeinket is próbáltad már?

**Üdvözletek:** Sok sikert! | Jó szórakozást kívánunk! | Alig várjuk, hogy gratulálhassunk neked!

---

### 6.4 Felhasználói aktivitás (inaktív felhasználók)
**Forrás:** `dj/lang/hu/mail.php` → `dc-user-inactive`

| Mező | Tartalom |
|---|---|
| **Tárgy (7 nap)** | Várunk vissza a DevChallenge-be! |
| **Tárgy (15 nap)** | Izgalmas kvízek várnak a DevChallenge-en! |
| **Tárgy (15 nap v2)** | Itt az idő, hogy kipróbáld magad a DevChallenge kvízeivel! |
| **Tárgy (30 nap)** | Már egy hónapja vár a DevChallenge! |

**7 napos üzenet:**
> Köszönjük, hogy már egy hete tagja vagy a DevChallenge közösségnek. Szomorúan látjuk, hogy ezidő alatt még csak pár kvízünket töltöttél ki. Az eddigi kitöltéseid alapján úgy gondoljuk, ezek a kvízek is érdekelhetnek:

---

### 6.5 Szériád veszélyben
**Forrás:** `dj/lang/hu/mail.php` → `dc-user-streak`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Veszélyben a szériád! |

**Üzenet:**
> Tölts ki egy kvízt, hogy ne vesszen el a szériád!

**CTA:** Kitöltök egy kvízt

---

### 6.6 Heti eredmények
**Forrás:** `dj/lang/hu/mail.php` → `dc-weekly-results`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Ilyen volt a heted a DevChallenge-en! |

**Üzenet:**
> Köszönjük, hogy ezen a héten is aktív voltál a DevChallenge oldalán! Kvízeinkre adott válaszadaiddal a következő eredményeket érted el:

**Statisztika formátum:**
> Válaszaiddal a **:category** témakör heti ranglistáján a **:weekly.** helyen állsz.
> Az örök ranglista helyezésed pedig a héten a következő: **:alltime.**
>
> A **:category** témakörben **:quizes** kvízt töltöttél ki.
> Válaszaid jelenlegi pontossága a **:category** témakörben: **:accuracy**

**Ösztönző:** Még jobb eredményekre vágysz? Itt egy kvíz, amivel feljebb juthatsz a rangsorban:  
**Üdvözlet:** Sok sikert kívánunk neked a jövő hétre is!

---

## 7. SZMD — Szerethető Munkahelyek Díj

### 7.1 Nevezés visszavonva
**Forrás:** `dj/lang/hu/mail.php` → `szmd-redact`

| Mező | Tartalom |
|---|---|
| **Tárgy** | SZMD:year nevezés visszavonása |

**Üzenet:**
> [:company](:url) cég a nevezését visszavonta a :year-es SZMD kapcsán

---

### 7.2 Újranevezés
**Forrás:** `dj/lang/hu/mail.php` → `szmd-renominate`

| Mező | Tartalom |
|---|---|
| **Tárgy** | SZMD:year újranevezés |

**Üzenet:**
> Remek hírünk van: [:company](:url) ismét beszállt a versenybe az idei Szerethető Munkahely címért!

---

### 7.3 SZMD promo kampány
**Forrás:** `dj/lang/hu/mail.php` → `szmd-promo`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Szerethető munkahely vagytok? Nevezz már most! |

**Üzenet:**
> Nyolcadik éve indítjuk útjára a Szerethető Munkahelyek versenyt :szmd_year-ben! Idén 200 magyar cég kapja meg majd a Szerethető Munkahelyek Díjat, melyek közül 8 céget választ majd ki a zsűri szakmai különdíjra.
>
> A Szerethető Munkahelyek verseny idei témája: **Mi így teszünk egy jobb világért**. Mutasd meg a szavazóknak, miért jó nálatok dolgozni...

---

## 8. Smart Bench Profile (SBP)

### 8.1 SBP profil nyilvánosságba kerülve
**Forrás:** `dj/lang/hu/mail.php` → `sbp-b2c`

| Mező | Tartalom |
|---|---|
| **Tárgy** | 😱 Most már közvetlenül is kaphatsz állásajánlatot! Frissítsd a profilod! ☝️ 😉 |

**Üzenet:**
> Örömmel értesítünk, hogy self-branding profilod bekerült a **nyilvános, cégek által elérhető adatbázisunkba**. Így a munkáltatók mostantól **közvetlenül kereshetnek meg állásajánlataikkal**. Ezért itt az idő, hogy frissítsd és még vonzóbbá tedd a profilod!

**CTA:** FRISSÍTEM A PROFILOM  
**Kikapcsolás opció:** Ha nem szeretnéd, hogy a profilod közvetlenül elérhető legyen a munkáltatók számára, egy kattintással ki tudod kapcsolni ezt a szolgáltatást a fiókodban!

---

### 8.2 SBP PDF elkészült
**Forrás:** `dj/lang/hu/mail.php` → `sbp-pdf`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Használd mostantól az egyedi önéletrajzod! |

**Üzenet:**
> Gratulálunk!
>
> Sikeresen kitöltötted a Self-Branding profilod, így nagyobb eséllyel pályázhatsz álmaid állására!
>
> ...ráadásként, elkészítettük neked **a pdf változatot** is, amit mostantól bátran használhatsz a hagyományos önéletrajzod helyett akár a :site-on, akár más állásportálon! **Nézd meg a csatolmányban!**

**Szlogen:** Tűnj ki a tömegből és találd meg álmaid állását!  
**CTA:** Kattints és mutatkozz be leendő munkaadódnak!

---

### 8.3 SBP profil elkészült (dj-api)
**Forrás:** `dj-api/lang/hu/mail.php` → `sbp_profile_created`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Self-Branding profilod elkészült! |

**Üzenet:**
> Szia :name!
>
> A DreamJobs AI-alapú önéletrajz-feldolgozód sikeresen létrehozta a Self-Branding profilodat.
>
> Ha úgy érzed, valami nem stimmel a profilodban, bármikor módosíthatod az adataidat.

**CTA:** Profilom megtekintése

---

### 8.4 SBP Talent Pool ingyenes kredit
**Forrás:** `dj/lang/hu/mail.php` → `sbp-search-free-credit`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Ajándék: Contact Credit |

**Üzenet:**
> Jó hírünk van! A megvásárolt Cappuccino / Cappuccino Extra hirdetéseidet amennyiben :date-ig beváltod, akkor Cappuccino esetén 2 db, Cappuccino Extra esetén 4db próba Contact Credit jár, amelyeket a DreamJo.bs Talent Pooljában tudsz felhasználni.
>
> Mi is ez?
>
> A Talent Pool egy **skill alapú jelöltkereső**, ahol a preferenciád szerint kereshetsz az aktív álláskeresők anonim bemutatkozói között. A jelölteket elmentheted és ha valakit megkeresnél egy állásajánlattal, akkor egy-egy contact credit beváltásával tudsz majd az adataihoz hozzáférni.
>
> A Contact Creditek **10-es és 35-ös csomagokban** lesznek megvásárolhatók a Dashboardon.

---

### 8.5 SBP Talent Pool launch értesítő
**Forrás:** `dj/lang/hu/mail.php` → `sbp-search-lunch`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Elindult a DreamJo.bs Talent Pool |

**Üzenet:**
> Jó hírünk van! Elindult a DreamJo.bs **Talent Pool** "pick and hire" szolgáltatása! Mi is ez? Egy **skill alapú jelöltkereső**, ahol a preferenciád szerint kereshetsz az aktív álláskeresők anonim bemutatkozói között...
>
> Bevezető akció: **2022. április 30-ig** minden futó **Cappuccino hirdetéshez 2 db Contact Credit**, minden futó **Cappuccino Extra hirdetéshez 4 db Contact Credit** próba csomagot adunk.

---

## 9. Megosztás és Meghívók

### 9.1 Link megosztása e-mailben (állás)
**Forrás:** `dj/lang/hu/mail.php` → `share-job`

| Mező | Tartalom |
|---|---|
| **Tárgy** | :from egy linket küldött neked |

**Üzenet:**
> :name egy álláshirdetés linket küldött neked a DreamJo.bs oldaláról

**CTA:** Nézd meg az álláshirdetést

---

### 9.2 Link megosztása e-mailben (cég)
**Forrás:** `dj/lang/hu/mail.php` → `share-company`

| Mező | Tartalom |
|---|---|
| **Tárgy** | :from egy linket küldött neked |

**Üzenet:**
> :name egy cég profil linket küldött neked a DreamJo.bs oldaláról

**CTA:** Nézd meg a cég profilját

---

### 9.3 Barát meghívása (IT kvíz)
**Forrás:** `dj/lang/hu/mail.php` → *(a sablonból: `mail.tests_friend_invite`)*

| Mező | Tartalom |
|---|---|
| **Tárgy** | :from meghívója |

---

## 10. Értékelések

### 10.1 Állás értékelés értesítő
**Forrás:** `dj/lang/hu/mail.php` → `job-review`  
**Sablon:** `mail.jobreviewcreated`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Új javaslat |

**Üzenet:**
> HR és Marketing szempontok szerint szemléztük az álláshirdetést és az alábbi javaslataink lennének:

**CTA:** Módosítom a hirdetésem  
**Javaslat szöveg:** Kérlek módosítsd a hirdetésed mihamarabb a nagyobb relevancia és a több jelentkező érdekében.  
**Köszönet:** Köszönjük, hogy nálunk hirdetsz!  
**Segítség:** Bármi további kérdésed felmerül, keresd a DreamJo.bs kapcsolattartód bizalommal.

---

## 11. Adminisztráció és Egyéb

### 11.1 Gold Profil érdeklődés (adminnak)
**Forrás:** `dj/lang/hu/mail.php` → *(sablon: `mail.gold_request_to_admin`)*

*(Admin belső értesítő — tárgy és tartalom az igénylési adatokból épül fel)*

---

### 11.2 Gold Profil érdeklődés (igénylőnek)
**Forrás:** `dj/lang/hu/mail.php` → `gold-request-b2b`

| Mező | Tartalom |
|---|---|
| **Tárgy** | Érdeklődés DreamJobs GOLD Profil iránt |

**Üzenet:**
> Örömmel vettük érdeklődésed GOLD Profil szolgáltatásunk iránt.
>
> Kollégánk hamarosan felveszi veled a kapcsolatot, hogy egyeztessétek a részleteket és segítsen a megrendelésben.

---

### 11.3 Karrier tanácsadás kérés (adminnak)
**Forrás:** `dj/lang/hu/mail.php` → *(sablon: `mail.admin_asked_for_career_advice`)*

| Mező | Tartalom |
|---|---|
| **Tárgy** | Karrier tanácsadás: :name |

*(Admin belső értesítő — a felhasználó neve, e-mail, megjegyzés és fájlok tartalmazza)*

---

### 11.4 Candidate Shortlist megrendelés
**Forrás:** `dj/lang/hu/mail.php` → *(sablon: `mail.candidate_shortlist`)*

| Mező | Tartalom |
|---|---|
| **Tárgy** | :name - Candidate Shortlist megrendelés |

*(Admin belső értesítő)*

---

### 11.5 Sourcing ajánlás
**Forrás:** `dj/lang/hu/mail.php` → `csl-recomendation`

**Üzenet:**
> Álláshirdetésed 14 napja fut.
> Amennyiben nem vagy elégedett a jelöltekkel, szeretnénk a figyelmedbe ajánlani SOURCING szolgáltatásunkat, melynek segítségével olyan leendő munkatársakat hozunk neked, akik nyitottak az ajánlatotokra.
> Ráadásul a hirdetési csomagod árát is visszakaphatod!
>
> Részletekért keresd Rókus az alábbi telefonszámon: +36 70 346 4330

---

### 11.6 Karácsonyi/Húsvéti promo (Egg Hunt / Xmas Hunt)
**Forrás:** `dj/lang/hu/mail.php` → `egghunt` / `xmashunt`

**Egg Hunt:**

| Mező | Tartalom |
|---|---|
| **Tárgy** | EGGHUNT akció! |

**Üzenet:**
> A húsvéti "EGGHUNT" akció keretén belül, **:discount%-os kupon** használatára vagy jogosult.
>
> Kuponkódod: **:coupon**
>
> Kupon felhasználható **Latte, Cappuccino, vagy Cappuccino Extra** hirdetésekre **2023 április 25-ig**.
>
> Nincs most épp nyitott pozíció Nálatok? Semmi gond! A kedvezményesen megvásárolt csomagodat **6 hónapig tudod felhasználni**.

**Üdvözlet:** Kellemes Húsvétot kívánunk

---

**Xmas Hunt (cégeknek):**

| Mező | Tartalom |
|---|---|
| **Tárgy** | XMASHUNT akció! |

**Üzenet:**
> A karácsonyi "XMASHUNT" akció keretén belül :discount %-os kupon használatára vagy jogosult.
>
> Kuponkódod: :coupon
>
> A kupon felhasználható korlátlan alkalommal az alábbi hirdetésekre: Latte, Cappuccino, Cappuccino Extra csomagokra.

**Üdvözlet:** Kellemes karácsonyi ünnepeket kívánunk!

---

### 11.7 Értesítési lábjegyzet elemek

| Elem | Szöveg |
|---|---|
| Leiratkozás | Szeretnél leiratkozni erről a listáról? Ide kattintva megteheted |
| Levelezési cím | Levelezési cimünk |
| Üdvözlés | Üdvözlettel |
| Köszönés | Üdv / Szia! / Kedves :name! / Szia :name! |
| Búcsú | Sok sikert kívánunk! / Üdv, |
| Aláírás csapat | A DreamJobs csapata |
| GDPR | Kérünk hogy a levélben kapott jelentkező adatokat bizalmasan, a hatályos adatvédelmi előírásoknak (GDPR) megfelelően kezeld. |

---

*Utolsó frissítés: 2026-05-26 — Automatizált kódbázis-audit alapján generálva.*
