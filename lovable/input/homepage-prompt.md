# PROMPT DLA LOVABLE — Strona główna SkyClinic
*Plik: lovable/homepage-prompt.md*
*Projekt: skyclinic.pl | marzec 2026*

---

## KONTEKST PROJEKTU

Budujesz stronę główną dla **SkyClinic** — premium kliniki medycyny estetycznej i transplantacji włosów działającej w Wrocławiu i Warszawie.

- **Stack:** React + Tailwind CSS
- **Cel strony:** Lead generation — formularz kontaktowy
- **Język:** Polski (pl-PL) — 100% tekstów po polsku, bez wyjątków
- **Tagline:** "Beginning of Beauty"
- **Filozofia:** "Przywracamy pewność siebie"
- **URL:** skyclinic.pl/

---

## STRUKTURA REPOZYTORIUM I DOSTĘPNE ZASOBY

Projekt korzysta z plików znajdujących się w repozytorium o następującej strukturze:

```
├── docs/                          ← specyfikacja, architektura, indeks
│   ├── SkyClinic_Specyfikacja_Strony_v1.1.md
│   └── INDEKS.md
├── content/
│   ├── zabiegi/                   ← 76 podstron .md (twarz/ cialo/ wlosy/ okolice-intymne/ laryngologia/)
│   └── potrzeby/                  ← 24 podstrony .md (twarz/ cialo/ wlosy/ okolice-intymne/ laryngologia/)
├── assets/
│   ├── logos/
│   │   └── Logo-2.png             ← LOGO SKYCLINIC — użyj w HEADER i FOOTER
│   └── images/                    ← 568 zdjęć w 60 podfolderach (po nazwie zabiegu)
│       ├── {nazwa-zabiegu}/
│       │   ├── {nazwa}_hero.jpg   ← zdjęcie główne zabiegu
│       │   ├── {nazwa}_opis_N.jpg ← zdjęcia opisowe
│       │   └── {nazwa}_przed-po_N.jpg ← zdjęcia przed/po
│       └── ...
├── brand/
│   └── SkyClinic BrandBook v3 2024 (1).pdf  ← pełny brandbook
├── lovable/input/                 ← prompty dla Lovable (ten plik)
├── lovable/exports/               ← eksporty z Lovable
└── ops/                           ← workflow i checklisty
```

### Dostępne zdjęcia hero dla wyróżnionych zabiegów (SEKCJA 6):

| Zabieg | Ścieżka do hero | Format |
|---|---|---|
| Przeszczep włosów FUE | `assets/images/przeszczep-wlosow-fue/przeszczep-wlosow-fue_hero.png` | PNG |
| Blefaroplastyka | `assets/images/blefaroplastyka/blefaroplastyka_hero.jpg` | JPG |
| SofWave | ⚠️ BRAK — użyj placeholdera | — |
| Dermapen | `assets/images/dermapen/dermapen_hero.jpg` | JPG |
| Fotona 4D | `assets/images/fotona/fotona_hero.jpg` | JPG |

### Logo:
- **Plik:** `assets/logos/Logo-2.png`
- Użyj w headerze (lewa strona) i footerze (kolumna 1)
- Wersja SVG i biała wersja — oczekuje na dostarczenie przez klinikę

### Brandbook:
- **Plik:** `brand/SkyClinic BrandBook v3 2024 (1).pdf`
- Kolory, typografia i zasady identyfikacji wizualnej zgodne z sekcją DESIGN SYSTEM poniżej

---

## DESIGN SYSTEM — OBOWIĄZKOWY

### Kolory (CSS variables)

```css
--color-dark-gray: #3C3C3C;
--color-mid-gray: #575757;
--color-light-gray: #C0C0C0;
--color-navy: #004080;
--color-yellow: #f4ba15;
--color-white: #FFFFFF;
--color-bg-light: #F8F8F8;
--color-bg-dark: #3C3C3C;
--color-text-primary: #3C3C3C;
--color-text-secondary: #575757;
--color-text-light: #FFFFFF;
```

### Typografia

- **Font:** Montserrat (Google Fonts) — załaduj 400, 500, 600, 700
- H1: 56–72px / Bold / line-height 1.1
- H2: 36–48px / Bold / line-height 1.2
- H3: 22–28px / SemiBold / line-height 1.3
- Body: 16px / Regular / line-height 1.65 / kolor #575757
- Overline: 11–12px / uppercase / letter-spacing 0.15em / kolor #004080
- Button: 14px / SemiBold / uppercase / letter-spacing 0.08em

### Layout

- Container max-width: 1280px
- Padding boczny: 24px mobile / 48px tablet / 80px desktop
- Section padding: 80px góra/dół desktop / 48px mobile
- Card gap: 24–32px
- Border-radius kart: 8px
- Border-radius przycisków: 4px

### Przyciski

**Primary:**
- Background: #004080 | Text: #FFFFFF
- Padding: 16px 32px | Border-radius: 4px
- Hover: background #003060 | Transition: 200ms ease

**Secondary (Outline):**
- Background: transparent | Border: 2px solid #004080 | Text: #004080
- Padding: 14px 30px | Border-radius: 4px
- Hover: background #004080, text #FFFFFF

### Karty zabiegów

- Background: #FFFFFF | Border: 1px solid #E8E8E8 | Border-radius: 8px
- Padding: 24px
- Hover: box-shadow 0 8px 32px rgba(0,0,0,0.10) + translateY(-2px) | Transition: 200ms

---

## HEADER — GLOBALNY (sticky)

```
[Logo SkyClinic: assets/logos/Logo-2.png — lewa strona]

Menu: Twoje potrzeby ▼ | Zabiegi | Wybrane usługi | O nas ▼ | Efekty

Prawa strona: [UMÓW WIZYTĘ — przycisk Primary] [tel. XXX XXX XXX]
```

- Sticky przy scrollowaniu
- Desktop: białe tło, dolna krawędź 1px solid #E8E8E8
- Mobile: hamburger (☰) po prawej → drawer slide-in z lewej
- "UMÓW WIZYTĘ" zawsze widoczny

**Megamenu "Twoje potrzeby" (hover na desktop):**
5 kolumn — TWARZ | CIAŁO | WŁOSY | LARYNGOLOGIA | OKOLICE INTYMNE

Linki w kolumnie TWARZ:
- Odmładzanie i lifting twarzy → /potrzeby/twarz/odmladanie-i-lifting-twarzy/
- Okolica oczu i powiek → /potrzeby/twarz/okolica-oczu-i-powiek/
- Zmarszczki mimiczne i botoks → /potrzeby/twarz/zmarszczki-mimiczne-i-botoks/
- Owal twarzy i żuchwa → /potrzeby/twarz/owal-twarzy-i-zuchwa/
- Usta → /potrzeby/twarz/usta/
- Jakość skóry i pory → /potrzeby/twarz/jakosc-skory-i-pory/
- Blizny → /potrzeby/twarz/blizny/
- Przebarwienia i koloryt → /potrzeby/twarz/przebarwienia-i-koloryt/
- Uszy → /potrzeby/twarz/uszy/

Linki w kolumnie CIAŁO:
- Modelowanie sylwetki i redukcja tłuszczu → /potrzeby/cialo/modelowanie-sylwetki-i-redukcja-tluszczu/
- Cellulit i jędrność → /potrzeby/cialo/cellulit-i-jedrnos/
- Blizny i rozstępy → /potrzeby/cialo/blizny-i-rozstepy/
- Zmiany skórne i paznokcie → /potrzeby/cialo/zmiany-skorne-i-paznokcie/
- Nadpotliwość → /potrzeby/cialo/nadpotliwosc/

Linki w kolumnie WŁOSY:
- Przeszczep włosów → /potrzeby/wlosy/przeszczep-wlosow/
- Leczenie wypadania włosów → /potrzeby/wlosy/leczenie-wypadania-wlosow/

Linki w kolumnie LARYNGOLOGIA:
- Leczenie chrapania → /potrzeby/laryngologia/leczenie-chrapania/
- Migdałki i nieprzyjemny zapach z ust → /potrzeby/laryngologia/migdalki-i-nieprzyjemny-zapach-z-ust/

Linki w kolumnie OKOLICE INTYMNE:
- Komfort i funkcja → /potrzeby/okolice-intymne/komfort-i-funkcja/
- Estetyka okolic intymnych → /potrzeby/okolice-intymne/estetyka-okolic-intymnych/
- Zabiegi chirurgiczne → /potrzeby/okolice-intymne/zabiegi-chirurgiczne-okolic-intymnych/

**Megamenu "O nas" (hover):**
- Klinika Wrocław → /o-nas/klinika-wroclaw/
- Klinika Warszawa → /o-nas/klinika-warszawa/
- Nasz zespół → /o-nas/nasz-zespol/
- Opinie pacjentów → /o-nas/opinie-pacjentow/
- Kariera → /o-nas/kariera/

---

## STRONA GŁÓWNA — 10 SEKCJI

### SEO HEAD

```
<title>SkyClinic — Klinika Medycyny Estetycznej i Transplantacji Włosów | Wrocław i Warszawa</title>
<meta name="description" content="SkyClinic to klinika medycyny estetycznej z Wrocławia i Warszawy. Przeszczep włosów FUE, botoks, lifting twarzy, SofWave i ponad 60 innych zabiegów. Umów bezpłatną konsultację." />
<link rel="canonical" href="https://skyclinic.pl/" />
<h1>Przywracamy pewność siebie</h1>  ← tylko jeden H1 na stronie
```

Schema.org MedicalClinic:
```json
{
  "@context": "https://schema.org",
  "@type": "MedicalClinic",
  "name": "SkyClinic",
  "description": "Klinika medycyny estetycznej i transplantacji włosów",
  "url": "https://skyclinic.pl",
  "telephone": "+48718898000",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "ul. Ołtaszyńska 71a",
    "addressLocality": "Wrocław",
    "postalCode": "53-034",
    "addressCountry": "PL"
  },
  "medicalSpecialty": ["Medycyna estetyczna", "Transplantacja włosów"]
}
```

---

### SEKCJA 1 — HERO

**Layout:** Pełna szerokość, tło ciemne (zdjęcie kliniki lub gradientowe #3C3C3C → #1a1a1a), tekst biały. Desktop: dwie kolumny — lewa tekst, prawa formularz. Mobile: stack pionowy.

**Teksty:**

```
H1 (jedyny na stronie):
Przywracamy pewność siebie

Subheadline (H2 wizualnie, semantycznie p lub span):
Klinika medycyny estetycznej i transplantacji włosów
Wrocław i Warszawa

Lead:
Ponad 10 lat doświadczenia, 67 procedur w ofercie, dwoje specjalistycznych klinik.
Zacznij od bezpłatnej konsultacji — dobierzemy metodę do Twoich potrzeb.
```

**6 kafelków obszarów** (grid 3×2 lub poziomy pasek pod H1):

| Kafelek | Ikona | Link |
|---|---|---|
| Twarz | ikona twarzy | /potrzeby/twarz/ |
| Ciało | ikona sylwetki | /potrzeby/cialo/ |
| Włosy | ikona włosów | /potrzeby/wlosy/ |
| Okolice intymne | ikona dyskretny | /potrzeby/okolice-intymne/ |
| Laryngologia | ikona gardła | /potrzeby/laryngologia/ |
| Konsultacje | ikona rozmowy | /kontakt/ |

Każdy kafelek: ikona + nazwa + hover efekt + klikalne.

**Formularz inline (prawa kolumna / pod kafelkami na mobile):**

```
Nagłówek formularza: Umów bezpłatną konsultację

Pola:
- Imię i nazwisko* (placeholder: "Imię i nazwisko")
- Numer telefonu* (placeholder: "Numer telefonu")
- Miasto* (dropdown: Wrocław / Warszawa)
- Checkbox: "Wyrażam zgodę na przetwarzanie danych osobowych zgodnie z polityką prywatności." (required)

Przycisk: "UMÓW BEZPŁATNĄ KONSULTACJĘ" (Primary, pełna szerokość)

Komunikat sukcesu: "Dziękujemy! Oddzwonimy w ciągu 24 godzin roboczych."
Błąd wymaganego pola: "To pole jest wymagane"
Błąd telefonu: "Podaj poprawny numer telefonu"
Błąd serwera: "Coś poszło nie tak. Spróbuj ponownie lub zadzwoń do nas."
```

---

### SEKCJA 2 — TRUST BAR (Pasek zaufania)

**Layout:** Pełna szerokość, tło #3C3C3C, tekst biały. 4 liczby w jednym rzędzie. Mobile: 2×2 grid.

```
Overline (nad całą sekcją, ukryty lub widoczny): brak

4 elementy:

[10+]          [67]              [8]              [2]
lat            procedur          specjalizacji    kliniki
doświadczenia  w ofercie
```

Każdy element: duża liczba Bold + etykieta Regular poniżej. Separatory pionowe między elementami na desktop.

---

### SEKCJA 3 — FILOZOFIA / MISJA

**Layout:** Tło białe lub #F8F8F8. Lewa kolumna: tekst. Prawa kolumna: 3 karty wartości.

```
Overline (p.overline, kolor #004080, uppercase):
NASZE PODEJŚCIE

H2:
Tu zaczyna się piękno

Lead (2–3 zdania, kolor #575757):
W SkyClinic wierzymy, że medycyna estetyczna to nie maskowanie — to przywracanie
pewności siebie. Każdy pacjent przychodzi do nas z inną historią i innymi potrzebami.
Dlatego zaczynamy zawsze od rozmowy, nie od zabiegu.
```

**3 karty wartości** (grid poziomy):

```
Karta 1:
[ikona — np. serce lub uścisk dłoni]
Uczciwość
Mówimy wprost co możemy osiągnąć, a czego nie. Bez obietnic bez pokrycia.

Karta 2:
[ikona — np. dyplom lub tarcza]
Profesjonalizm
Nasi lekarze to specjaliści z wieloletnim doświadczeniem i udokumentowanymi wynikami.

Karta 3:
[ikona — np. strzałka w górę lub roślina]
Rozwój
Stale inwestujemy w najnowsze technologie i szkolenia, żeby oferować skuteczne metody.
```

Karty: białe tło, border 1px #E8E8E8, border-radius 8px, padding 24px, ikona w kolorze #004080.

---

### SEKCJA 4 — PROCES (Jak działamy)

**Layout:** Tło #F8F8F8. 4 kroki w poziomie (desktop) lub pionowo (mobile). Strzałki/linia łącząca kroki.

```
Overline: JAK DZIAŁAMY
H2: Twoja droga do efektu

Krok 1:
[numer 01 lub ikona rozmowy]
Konsultacja
Zaczynamy od dokładnej rozmowy o Twoich potrzebach i oczekiwaniach. Oceniamy stan zdrowia i dobieramy metodę.

Krok 2:
[numer 02 lub ikona książki]
Edukacja
Tłumaczymy zabieg — jak działa, czego się spodziewać, jakie są efekty i jak wygląda rekonwalescencja.

Krok 3:
[numer 03 lub ikona stetoskopu]
Zabieg
Przeprowadzamy zabieg w sterylnych warunkach, dbając o Twój komfort na każdym etapie.

Krok 4:
[numer 04 lub ikona checkmark]
Opieka pozabiegowa
Jesteśmy z Tobą po zabiegu — kontrole, odpowiedzi na pytania, wsparcie w trakcie gojenia i rekonwalescencji.
```

Styl numerów: Bold, duże, kolor #004080 lub #C0C0C0 jako tło cyfry.

---

### SEKCJA 5 — POPULARNE POTRZEBY

**Layout:** Tło białe. Grid 3×2 (6 kart). Mobile: 1 kolumna lub 2×3.

```
Overline: ZACZNIJ OD SWOJEJ POTRZEBY
H2: Co Cię do nas sprowadza?
```

**6 kart potrzeb:**

```
Karta 1:
[zdjęcie placeholder — twarz kobiety]
Overline: TWARZ
Nazwa: Odmładzanie i lifting twarzy
CTA link: "Poznaj metody" → /potrzeby/twarz/odmladanie-i-lifting-twarzy/

Karta 2:
[zdjęcie placeholder — skóra głowy / włosy]
Overline: WŁOSY
Nazwa: Przeszczep włosów
CTA link: "Poznaj metody" → /potrzeby/wlosy/przeszczep-wlosow/

Karta 3:
[zdjęcie placeholder — sylwetka]
Overline: CIAŁO
Nazwa: Modelowanie sylwetki
CTA link: "Poznaj metody" → /potrzeby/cialo/modelowanie-sylwetki-i-redukcja-tluszczu/

Karta 4:
[zdjęcie placeholder — skóra twarzy zbliżenie]
Overline: TWARZ
Nazwa: Jakość skóry i pory
CTA link: "Poznaj metody" → /potrzeby/twarz/jakosc-skory-i-pory/

Karta 5:
[zdjęcie placeholder — sypialnia / para śpiąca]
Overline: LARYNGOLOGIA
Nazwa: Leczenie chrapania
CTA link: "Poznaj metody" → /potrzeby/laryngologia/leczenie-chrapania/

Karta 6:
[zdjęcie placeholder — dyskretne]
Overline: OKOLICE INTYMNE
Nazwa: Estetyka okolic intymnych
CTA link: "Poznaj metody" → /potrzeby/okolice-intymne/estetyka-okolic-intymnych/
```

Styl karty: zdjęcie górna połowa (aspect ratio 4:3), białe tło, overline #004080 uppercase mały, nazwa H3 Bold, link "Poznaj metody" ze strzałką →. Hover: lekki cień + translateY(-2px).

---

### SEKCJA 6 — WYRÓŻNIONE ZABIEGI

**Layout:** Tło #F8F8F8. 5 kart w poziomie (desktop może być scroll poziomy lub grid). Mobile: karuzela lub 1 kolumna.

```
Overline: NASZE SPECJALNOŚCI
H2: Zabiegi, z których jesteśmy znani
```

**5 kart zabiegów:**

```
Karta 1:
[assets/images/przeszczep-wlosow-fue/przeszczep-wlosow-fue_hero.png]
Przeszczep włosów FUE
Trwałe uzupełnienie owłosienia metodą manualną. Lider przeszczepów w Polsce.
[przycisk Secondary: "DOWIEDZ SIĘ WIĘCEJ"] → /zabiegi/przeszczep-wlosow-fue/

Karta 2:
[assets/images/blefaroplastyka/blefaroplastyka_hero.jpg]
Blefaroplastyka
Chirurgiczna korekta opadających powiek górnych i dolnych. Trwały, naturalny efekt.
[przycisk Secondary: "DOWIEDZ SIĘ WIĘCEJ"] → /zabiegi/blefaroplastyka/

Karta 3:
[⚠️ BRAK hero — użyj placeholdera szarego z tekstem "SofWave"]
SofWave
Nieinwazyjny lifting ultradźwiękowy twarzy. Bez operacji, bez rekonwalescencji.
[przycisk Secondary: "DOWIEDZ SIĘ WIĘCEJ"] → /zabiegi/sofwave/

Karta 4:
[assets/images/dermapen/dermapen_hero.jpg]
Dermapen
Mikroigłowa stymulacja regeneracji skóry. Poprawa tekstury, redukcja porów i blizn.
[przycisk Secondary: "DOWIEDZ SIĘ WIĘCEJ"] → /zabiegi/dermapen/

Karta 5:
[assets/images/fotona/fotona_hero.jpg]
Fotona 4D
Laserowe odmładzanie, lifting i rewitalizacja twarzy w jednej sesji.
[przycisk Secondary: "DOWIEDZ SIĘ WIĘCEJ"] → /zabiegi/fotona/
```

---

### SEKCJA 7 — NASZ ZESPÓŁ

**Layout:** Tło białe. Karty lekarzy w rzędzie (3–4 na desktop). Mobile: karuzela lub 2 kolumny.

```
Overline: NASZ ZESPÓŁ
H2: Lekarze, którym ufają tysiące pacjentów

[placeholder — karty lekarzy]
Każda karta:
- Zdjęcie portretowe (kwadrat lub lekko zaokrąglone)
- Imię i nazwisko (H3)
- Specjalizacja (body, kolor #575757)
- [opcjonalnie: CTA "Umów wizytę"]

Na dole sekcji:
Przycisk Secondary (wyśrodkowany): "POZNAJ CAŁY ZESPÓŁ" → /o-nas/nasz-zespol/
```

Uwaga: zdjęcia i biografie lekarzy dostarcza klinika. Użyj placeholderów z initials lub szarych avatarów.

---

### SEKCJA 8 — OPINIE PACJENTÓW

**Layout:** Tło #F8F8F8. Karuzela opinii (auto-play lub strzałki).

```
Overline: OPINIE PACJENTÓW
H2: Co mówią nasi pacjenci
```

**Przykładowe placeholdery kart opinii (do zastąpienia prawdziwymi):**

```
Karta opinii:
⭐⭐⭐⭐⭐
"[Treść opinii — placeholder. Prawdziwe opinie dostarcza klinika z Google/Znany Lekarz]"
Anna K. — zabieg: SofWave
```

Każda karta: gwiazdki (żółte #f4ba15), cytat w cudzysłowie, imię + zabieg poniżej, szare tło karty lub białe z cieniem. Min. 3–4 karty widoczne/przesuwalnia.

---

### SEKCJA 9 — DWE KLINIKI

**Layout:** Tło białe. Dwie równe kolumny desktop. Mobile: stack pionowy.

```
H2: Dwie kliniki — jedno doświadczenie
```

**Kolumna lewa — Wrocław:**
```
[zdjęcie kliniki Wrocław — placeholder]
SkyClinic Wrocław
ul. Ołtaszyńska 71a, 53-034 Wrocław
tel. +48 71 889 80 00
[przycisk Secondary: "ZOBACZ KLINIKĘ"] → /o-nas/klinika-wroclaw/
```

**Kolumna prawa — Warszawa:**
```
[zdjęcie kliniki Warszawa — placeholder]
SkyClinic Warszawa
[adres Warszawa — do uzupełnienia przez klinikę]
[tel. Warszawa — do uzupełnienia przez klinikę]
[przycisk Secondary: "ZOBACZ KLINIKĘ"] → /o-nas/klinika-warszawa/
```

---

### SEKCJA 10 — FORMULARZ KONTAKTOWY

**Layout:** Tło #F8F8F8. Dwie kolumny desktop: lewa formularz, prawa dane kontaktowe. Mobile: stack pionowy.

```
Overline: KONTAKT
H2: Masz pytania? Doradzimy.
```

**Formularz pełny (lewa kolumna):**

```
Pola:
- Imię i nazwisko* (placeholder: "Imię i nazwisko")
- Numer telefonu* (placeholder: "Numer telefonu")
- Adres e-mail (placeholder: "Adres e-mail")
- Czego dotyczy zapytanie? (dropdown):
  Twarz | Ciało | Włosy | Okolice intymne | Laryngologia | Inne
- Treść wiadomości (textarea, placeholder: "W czym możemy Ci pomóc?")
- Preferowana lokalizacja* (radio lub dropdown: Wrocław / Warszawa / Dowolna)
- Checkbox RODO (required): "Wyrażam zgodę na przetwarzanie danych osobowych zgodnie z polityką prywatności."
- Checkbox marketing (optional): "Wyrażam zgodę na otrzymywanie informacji marketingowych."

Przycisk: "WYŚLIJ WIADOMOŚĆ" (Primary, pełna szerokość)

Sukces: "Wiadomość wysłana! Odezwiemy się w ciągu 24 godzin."
```

**Dane kontaktowe (prawa kolumna):**

```
SkyClinic Wrocław
ul. Ołtaszyńska 71a
53-034 Wrocław
tel. +48 71 889 80 00

SkyClinic Warszawa
[adres — do uzupełnienia]
[tel. — do uzupełnienia]

[opcjonalnie: mapa Google Maps embed]
```

---

## FOOTER — GLOBALNY

**Layout:** Tło #3C3C3C. Tekst #FFFFFF. 4 kolumny desktop. Mobile: stack pionowy.

```
Kolumna 1: Logo (assets/logos/Logo-2.png) + tagline "Beginning of Beauty" + social icons (FB, IG, TikTok, LinkedIn)

Kolumna 2: Zabiegi (6–8 linków do popularnych zabiegów)
- Przeszczep włosów FUE → /zabiegi/przeszczep-wlosow-fue/
- SofWave → /zabiegi/sofwave/
- Blefaroplastyka → /zabiegi/blefaroplastyka/
- Toksyna botulinowa → /zabiegi/toksyna-botulinowa/
- Dermapen → /zabiegi/dermapen/
- Fotona 4D → /zabiegi/fotona/

Kolumna 3: O nas
- Klinika Wrocław → /o-nas/klinika-wroclaw/
- Klinika Warszawa → /o-nas/klinika-warszawa/
- Nasz zespół → /o-nas/nasz-zespol/
- Opinie pacjentów → /o-nas/opinie-pacjentow/
- Kariera → /o-nas/kariera/

Kolumna 4: Kontakt
Wrocław: ul. Ołtaszyńska 71a | tel. +48 71 889 80 00
Warszawa: [adres i tel. do uzupełnienia]

Dół footera (pełna szerokość, border-top 1px #575757):
© 2026 SkyClinic Sp. z o.o.
[Polityka prywatności] [Regulamin] [Cookies]
```

Linki w footerze: kolor #C0C0C0, hover kolor #FFFFFF.

---

## WYMAGANIA TECHNICZNE OBOWIĄZKOWE

### Performance
- Lazy loading wszystkich zdjęć z wyjątkiem hero (LCP)
- Format zdjęć: WebP z fallback JPG
- Preload Google Fonts: Montserrat 400, 500, 600, 700
- Core Web Vitals target: LCP < 2.5s, CLS < 0.1

### Dostępność (WCAG 2.1 AA)
- Kontrast minimum 4.5:1 dla tekstu
- Focus visible na wszystkich elementach interaktywnych
- Semantyczny HTML: nav, main, section, article, footer
- aria-labels na przyciskach ikonowych
- Skip-to-main-content link

### Mobile
- Breakpoints: 375px | 768px | 1024px | 1280px
- Mobile-first CSS
- Touch targets minimum 44×44px
- Karuzele swipe-friendly

### RODO
- Cookie consent banner przed załadowaniem analityki
- Tekst bannera: "Ta strona używa plików cookie, aby zapewnić najlepszą jakość usług."
- Przyciski: "Akceptuję wszystkie" (Primary) | "Dostosuj ustawienia" (Secondary) | "Odrzuć opcjonalne" (link)

### Formularze — wszystkie komunikaty po polsku
```
Błąd wymaganego pola: "To pole jest wymagane"
Błąd email: "Podaj poprawny adres e-mail"
Błąd telefonu: "Podaj poprawny numer telefonu"
Sukces: "Dziękujemy! Oddzwonimy w ciągu 24 godzin."
Ładowanie: "Wysyłanie..."
Błąd serwera: "Coś poszło nie tak. Spróbuj ponownie lub zadzwoń do nas."
```

---

## DANE CZEKAJĄCE NA DOSTARCZENIE PRZEZ KLINIKĘ

Poniższe elementy są placeholderami — wymagają dostarczenia przez SkyClinic przed uruchomieniem:

- [ ] Logo SVG (wersja pozioma biała + ciemnoszara)
- [ ] Zdjęcia portretowe lekarzy z imionami i specjalizacjami
- [ ] Zdjęcia wnętrz obu klinik (Wrocław + Warszawa)
- [ ] Adres i telefon kliniki Warszawa
- [ ] Godziny otwarcia obu klinik
- [ ] Opinie pacjentów (min. 6, źródło: Google lub Znany Lekarz)
- [ ] Zdjęcia hero do sekcji 1 (tło)
- [ ] Social media linki (FB, IG, TikTok, LinkedIn)

---

*Prompt: lovable/input/homepage-prompt.md*
*Na podstawie: docs/SkyClinic_Specyfikacja_Strony_v1.1.md + brand/SkyClinic BrandBook v3 2024 (1).pdf + treści z content/ + Miro board uXjVGsGdcOk*
