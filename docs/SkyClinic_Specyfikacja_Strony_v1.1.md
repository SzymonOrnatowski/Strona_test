# SkyClinic — Specyfikacja Strony Internetowej v1.1
*Dokument techniczny dla developera / Lovable.*  
*Zmiany v1.1: architektura /potrzeby/, megamenu, SEO, URL bez polskich znaków, teksty PL, relacje many-to-many*

---

## 1. INFORMACJE O PROJEKCIE

| Parametr | Wartość |
|---|---|
| Klient | SkyClinic (SkyClinic Sp. z o.o.) |
| Domena | skyclinic.pl |
| Język strony | Polski (pl-PL) — WSZYSTKIE teksty po polsku |
| Cel główny | Lead generation — formularz kontaktowy |
| Lokalizacje | Wrocław (główna) + Warszawa |
| Narzędzie | Lovable (React + Tailwind) |
| Tagline | "Beginning of Beauty" |
| Filozofia | "Przywracamy pewność siebie" |

> **WAŻNE:** Wszystkie teksty widoczne dla użytkownika — etykiety przycisków, komunikaty błędów formularzy, placeholdery pól, komunikaty sukcesu, napisy "Wczytywanie...", tooltips — muszą być po polsku.

---

## 2. DESIGN SYSTEM

### 2.1 Kolory

```css
/* Kolory podstawowe logo */
--color-dark-gray: #3C3C3C;     /* Ciemna szarość — kolor tekstu, logo */
--color-mid-gray: #575757;      /* Średnia szarość — elementy pomocnicze */
--color-light-gray: #C0C0C0;    /* Jasna szarość — tła, divisory */

/* Kolor akcentu */
--color-navy: #004080;          /* Granat — linki, nagłówki sekcji, CTA secondary */

/* Kolory pomocnicze */
--color-yellow: #f4ba15;        /* Złoty — badges, wyróżnienia */

/* Tła */
--color-white: #FFFFFF;
--color-bg-light: #F8F8F8;
--color-bg-dark: #3C3C3C;

/* Tekst */
--color-text-primary: #3C3C3C;
--color-text-secondary: #575757;
--color-text-light: #FFFFFF;
```

**Zasady:**
- Tło domyślne: biały / alternujący z #F8F8F8
- Przycisk CTA główny: #004080 z białym tekstem
- Linki i akcenty: #004080
- H2 sekcji: #3C3C3C
- Label powyżej H2 (overline): #004080 uppercase, letter-spacing 0.15em
- Dekoracje (kwadraty brand): #C0C0C0 + #004080

### 2.2 Typografia

**Czcionka: Montserrat** (Google Fonts — zamiennik Azo Sans z brand booka)

```
Montserrat Regular 400   — body text, opisy
Montserrat Medium 500    — subheadingi, etykiety
Montserrat SemiBold 600  — H3, H4, przyciski
Montserrat Bold 700      — H1, H2, nagłówki hero
```

**Skala:**
```
H1:           56-72px / 1.1 / Bold / #3C3C3C lub #FFFFFF
H2:           36-48px / 1.2 / Bold / #3C3C3C
H3:           22-28px / 1.3 / SemiBold / #3C3C3C
H4:           18-20px / 1.4 / SemiBold
Body:         16px / 1.65 / Regular / #575757
Body small:   14px / 1.6 / Regular / #575757
Overline:     11-12px / uppercase / letter-spacing 0.15em / #004080
Button:       14px / SemiBold / uppercase / letter-spacing 0.08em
```

### 2.3 Spacing & Layout

```
Container max-width:  1280px
Padding boczny:       24px (mobile) / 48px (tablet) / 80px (desktop)
Section padding:      80px top/bottom (desktop) / 48px (mobile)
Card gap:             24-32px
Border-radius karty:  8px
Border-radius button: 4px
```

### 2.4 Komponenty UI

#### Przycisk główny (Primary)
```
Background: #004080 | Text: #FFFFFF
Font: Montserrat SemiBold 14px uppercase | Letter-spacing: 0.08em
Padding: 16px 32px | Border-radius: 4px
Hover: background #003060 | Transition: 200ms ease
Tekst przykładowy: "UMÓW KONSULTACJĘ", "SPRAWDŹ OFERTĘ"
```

#### Przycisk dodatkowy (Secondary / Outline)
```
Background: transparent | Border: 2px solid #004080 | Text: #004080
Padding: 14px 30px | Border-radius: 4px
Hover: background #004080, text #FFFFFF
Tekst przykładowy: "DOWIEDZ SIĘ WIĘCEJ", "CENNIK"
```

#### Karta zabiegu
```
Background: #FFFFFF | Border: 1px solid #E8E8E8 | Border-radius: 8px
Padding: 24px
Hover: box-shadow: 0 8px 32px rgba(0,0,0,0.10), translateY(-2px) | Transition: 200ms
```

#### Komunikaty formularza (po polsku)
```
Błąd pola wymaganego:     "To pole jest wymagane"
Błąd formatu email:        "Podaj poprawny adres e-mail"
Błąd formatu telefonu:     "Podaj poprawny numer telefonu"
Sukces wysłania:           "Dziękujemy! Oddzwonimy w ciągu 24 godzin."
Błąd serwera:              "Coś poszło nie tak. Spróbuj ponownie lub zadzwoń do nas."
Placeholder imię:          "Imię i nazwisko"
Placeholder telefon:       "Numer telefonu"
Placeholder email:         "Adres e-mail"
Placeholder wiadomość:     "W czym możemy Ci pomóc?"
Label przycisku ładowania: "Wysyłanie..."
```

---

## 3. ARCHITEKTURA SERWISU I URL

### 3.1 Zasady budowania URL

- Tylko małe litery
- Słowa rozdzielone myślnikiem `-`
- Bez polskich znaków: ą→a, ę→e, ó→o, ś→s, ł→l, ż→z, ź→z, ć→c, ń→n, ź→z
- Bez spacji, bez podkreślników
- Przykład: "Odmładzanie i lifting twarzy" → `odmładzanie-i-lifting-twarzy` → `odmładzanie` już po usunięciu: `odmładzanie` → `odmladanie-i-lifting-twarzy`

**Konwersja polskich znaków:**
```
ą → a   ć → c   ę → e   ł → l   ń → n
ó → o   ś → s   ź → z   ż → z
```

### 3.2 Pełna mapa URL serwisu

```
skyclinic.pl/
│
├── /                              ← Strona główna
│
├── /potrzeby/                     ← Lista grup potrzeb (landing obszarów)
│   ├── /potrzeby/twarz/           ← Lista potrzeb dla twarzy
│   │   ├── /potrzeby/twarz/odmładzanie-i-lifting-twarzy/
│   │   ├── /potrzeby/twarz/okolica-oczu-i-powiek/
│   │   ├── /potrzeby/twarz/zmarszczki-mimiczne-i-botoks/
│   │   ├── /potrzeby/twarz/owal-twarzy-i-zuchwa/
│   │   ├── /potrzeby/twarz/usta/
│   │   ├── /potrzeby/twarz/jakosc-skory-i-pory/
│   │   ├── /potrzeby/twarz/blizny/
│   │   ├── /potrzeby/twarz/przebarwienia-i-koloryt/
│   │   └── /potrzeby/twarz/uszy/
│   │
│   ├── /potrzeby/cialo/           ← Lista potrzeb dla ciała
│   │   ├── /potrzeby/cialo/modelowanie-sylwetki-i-redukcja-tluszczu/
│   │   ├── /potrzeby/cialo/cellulit-i-jedrnos/
│   │   ├── /potrzeby/cialo/blizny-i-rozstepy/
│   │   ├── /potrzeby/cialo/zmiany-skorne-i-paznokcie/
│   │   └── /potrzeby/cialo/nadpotliwosc/
│   │
│   ├── /potrzeby/wlosy/
│   │   ├── /potrzeby/wlosy/przeszczep-wlosow/
│   │   └── /potrzeby/wlosy/leczenie-wypadania-wlosow/
│   │
│   ├── /potrzeby/okolice-intymne/
│   │   ├── /potrzeby/okolice-intymne/komfort-i-funkcja/
│   │   ├── /potrzeby/okolice-intymne/estetyka-okolic-intymnych/
│   │   └── /potrzeby/okolice-intymne/zabiegi-chirurgiczne-okolic-intymnych/
│   │
│   └── /potrzeby/laryngologia/
│       ├── /potrzeby/laryngologia/leczenie-chrapania/
│       └── /potrzeby/laryngologia/migdalki-i-nieprzyjemny-zapach-z-ust/
│
├── /zabiegi/                      ← Katalog wszystkich zabiegów (index)
│   └── /zabiegi/[slug-zabiegu]/   ← ×67 podstron zabiegowych
│
├── /wybrane-uslugi/               ← Strona wybranych usług (landing)
│
├── /o-nas/
│   ├── /o-nas/klinika-wroclaw/
│   ├── /o-nas/klinika-warszawa/
│   ├── /o-nas/nasz-zespol/
│   ├── /o-nas/opinie-pacjentow/
│   └── /o-nas/kariera/
│
├── /efekty-pacjentow/
├── /promocje/
├── /wiedza/
│   └── /wiedza/[slug-artykulu]/
└── /kontakt/
```

### 3.3 Relacja many-to-many: Zabiegi ↔ Potrzeby

Wiele zabiegów przypisanych jest do wielu potrzeb i obszarów jednocześnie. Zasady:

- Każdy zabieg ma **jedną kanoniczną podstronę** pod `/zabiegi/[slug]/`
- Podstrona potrzeby **linkuje** do tych podstron zabiegów (nie duplikuje treści)
- Podstrona zabiegu w sekcji "Ten zabieg pomaga przy:" **linkuje z powrotem** do powiązanych potrzeb
- Przykład: Fotona (canonical: `/zabiegi/fotona/`) jest linkowana z `/potrzeby/twarz/odmładzanie-i-lifting-twarzy/`, `/potrzeby/twarz/jakosc-skory-i-pory/`, `/potrzeby/twarz/przebarwienia-i-koloryt/`, `/potrzeby/twarz/usta/`, `/potrzeby/twarz/okolica-oczu-i-powiek/`

**Zabiegi wieloobszarowe** (ten sam zabieg w ciało i twarz) — tworzymy **osobne podstrony** z odrębnym contentem dostosowanym do obszaru:

| Zabieg | Podstrona twarz | Podstrona ciało |
|---|---|---|
| EXION | /zabiegi/exion/ | /zabiegi/exion-cialo/ |
| Endermologia | /zabiegi/endermologia/ | /zabiegi/endermologia-cialo/ |
| Epilacja laserowa | /zabiegi/epilacja-laserowa-twarz/ | /zabiegi/epilacja-laserowa/ |
| Laseroterapia | /zabiegi/laseroterapia-odmładzanie/ | /zabiegi/laseroterapia-cialo/ |
| Laserowe usuwanie naczynek | /zabiegi/laserowe-usuwanie-naczynek/ | /zabiegi/laserowe-usuwanie-naczynek-cialo/ |
| Fotona | /zabiegi/fotona/ | /zabiegi/fotona-cialo/ |
| StarWalker | /zabiegi/starwalker/ | /zabiegi/starwalker-cialo/ |
| Dermapen | /zabiegi/dermapen/ | /zabiegi/dermapen-skora-glowy/ |
| Komórki macierzyste CGF | /zabiegi/komorki-macierzyste-cgf/ | /zabiegi/komorki-macierzyste-cgf-wlosy/ |
| Osocze PRP | /zabiegi/osocze-bogatoplytkowe-prp/ | /zabiegi/osocze-bogatoplytkowe-prp-wlosy/ |
| Toksyna botulinowa | /zabiegi/toksyna-botulinowa/ | /zabiegi/toksyna-botulinowa-nadpotliwosc/ |

---

## 4. NAWIGACJA

### 4.1 Header

```
[Logo SkyClinic horizontal]  |  Twoje potrzeby ▼  |  Zabiegi  |  Wybrane usługi  |  O nas ▼  |  Efekty  |  [UMÓW WIZYTĘ]  [tel. XXX XXX XXX]
```

- Sticky przy scrollowaniu
- Na desktop: tło białe, dolna krawędź 1px #E8E8E8
- Na mobile: hamburger z prawej strony, drawer z lewej
- "UMÓW WIZYTĘ" = przycisk Primary zawsze widoczny

### 4.2 Megamenu "Twoje potrzeby" (hover)

Rozwija się po najechaniu na "Twoje potrzeby". Struktura: 5 kolumn = 5 grup obszarów.

```
┌─────────────────────────────────────────────────────────────────┐
│  TWARZ              CIAŁO                WŁOSY                  │
│  • Odmładzanie      • Modelowanie        • Przeszczep włosów    │
│  • Okolica oczu       sylwetki           • Leczenie wypadania   │
│  • Zmarszczki       • Cellulit i           włosów               │
│    mimiczne           jędrność                                  │
│  • Owal twarzy      • Blizny i           LARYNGOLOGIA           │
│  • Usta               rozstępy          • Leczenie chrapania    │
│  • Jakość skóry     • Zmiany skórne     • Migdałki              │
│  • Blizny           • Nadpotliwość                              │
│  • Przebarwienia                        OKOLICE INTYMNE         │
│  • Uszy             [Przejdź do ciała]  • Komfort i funkcja     │
│  [Przejdź do twarzy]                   • Estetyka              │
│                                         • Zabiegi chirurgiczne  │
└─────────────────────────────────────────────────────────────────┘
```

Każda pozycja = link do `/potrzeby/[obszar]/[slug-potrzeby]/`  
Każdy nagłówek kolumny (TWARZ, CIAŁO itd.) = link do `/potrzeby/[obszar]/`  
Przycisk "Przejdź do twarzy" = link do `/potrzeby/twarz/`

### 4.3 "Zabiegi" w menu — bez rozwijania

Kliknięcie przenosi bezpośrednio na `/zabiegi/` (katalog zabiegów z filtrowaniem). Brak megamenu dla tej pozycji.

### 4.4 Megamenu "O nas" (hover)

Prosta lista bez kolumn:
```
• Klinika Wrocław
• Klinika Warszawa
• Nasz zespół
• Opinie pacjentów
• Kariera
```

---

## 5. SEO — WYTYCZNE GLOBALNE

### 5.1 Format title i meta description

**Strona główna:**
```
Title:            SkyClinic — Klinika Medycyny Estetycznej i Transplantacji Włosów | Wrocław i Warszawa
Meta description: SkyClinic to klinika medycyny estetycznej z Wrocławia i Warszawy. Przeszczep włosów FUE, botoks, lifting twarzy, SofWave i ponad 60 innych zabiegów. Umów bezpłatną konsultację.
```

**Podstrona zabiegu:**
```
Title:            [Nazwa zabiegu] — cena, efekty, opis | SkyClinic Wrocław i Warszawa
Meta description: Dowiedz się więcej o [nazwa zabiegu] w SkyClinic. Doświadczeni specjaliści, nowoczesny sprzęt, naturalne efekty. ✓ Wrocław ✓ Warszawa. Umów bezpłatną konsultację.
Przykład:         SofWave — lifting ultradźwiękowy twarzy | SkyClinic Wrocław i Warszawa
```

**Podstrona potrzeby:**
```
Title:            [Nazwa potrzeby] — skuteczne metody leczenia | SkyClinic
Meta description: Szukasz rozwiązania na [potrzeba]? W SkyClinic oferujemy [X] sprawdzonych metod. Wrocław i Warszawa. Umów bezpłatną konsultację.
Przykład:         Odmładzanie i lifting twarzy — skuteczne metody | SkyClinic Wrocław
```

**Strona lokalizacji:**
```
Title:            SkyClinic Wrocław — Klinika Medycyny Estetycznej | ul. Ołtaszyńska 71a
Meta description: SkyClinic Wrocław — klinika medycyny estetycznej na ul. Ołtaszyńskiej 71a. Transplantacja włosów, botoks, laser. Zadzwoń: [tel].
```

### 5.2 Zasady H1 i H2

- **H1**: dokładnie jeden na każdej podstronie, opisuje tematykę podstrony, zawiera słowo kluczowe
- **H2**: nagłówki głównych sekcji (po 1-2 na sekcję), powinny zawierać powiązane słowa kluczowe
- Nagłówki dekoracyjne (np. label/overline powyżej H2) używają elementu `<p class="overline">` lub `<span>` — NIE `<h>` tagu

**Przykłady H1 i H2 dla podstrony zabiegu (SofWave):**
```
H1: SofWave — nieinwazyjny lifting twarzy ultradźwiękami
H2 sekcji efektów:   Efekty zabiegu SofWave — zdjęcia przed i po
H2 sekcji opisu:     Na czym polega zabieg SofWave?
H2 cennika:          Cennik zabiegu SofWave
H2 FAQ:              Najczęstsze pytania o SofWave
H2 opinii:           Opinie pacjentów po zabiegu SofWave
```

**Przykłady H1 i H2 dla podstrony potrzeby:**
```
H1: Odmładzanie i lifting twarzy — poznaj skuteczne metody
H2: Kiedy to dotyczy Ciebie?
H2: Metody, które stosujemy w SkyClinic
H2: Efekty naszych pacjentów
H2: Często zadawane pytania o odmładzanie twarzy
```

### 5.3 Breadcrumbs

Widoczne na każdej podstronie poniżej headera. Format breadcrumb:

```
Strona główna > [Obszar lub kategoria] > [Nazwa strony]
```

**Przykłady:**
```
Strona główna > Twoje potrzeby > Twarz > Odmładzanie i lifting twarzy
Strona główna > Zabiegi > SofWave
Strona główna > Zabiegi > Przeszczep włosów FUE
Strona główna > O nas > Klinika Wrocław
```

Implementacja: znacznik HTML + JSON-LD `schema.org/BreadcrumbList` w `<head>`.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type": "ListItem", "position": 1, "name": "Strona główna", "item": "https://skyclinic.pl/"},
    {"@type": "ListItem", "position": 2, "name": "Zabiegi", "item": "https://skyclinic.pl/zabiegi/"},
    {"@type": "ListItem", "position": 3, "name": "SofWave", "item": "https://skyclinic.pl/zabiegi/sofwave/"}
  ]
}
```

### 5.4 Alt text dla zdjęć

Zasada: alt opisuje **zawartość** zdjęcia + kontekst strony, bez "zdjęcie", "obrazek", "foto".

**Wzorzec alt text:**
```
Zdjęcia efektów zabiegu (przed/po):
alt="Efekt zabiegu SofWave — lifting twarzy, wyniki po 1 sesji, pacjentka SkyClinic Wrocław"
alt="Przed i po zabiegu botoksu — wygładzenie zmarszczek mimicznych, klinika SkyClinic"

Zdjęcia lekarzy:
alt="Dr [Imię Nazwisko] — specjalista medycyny estetycznej, SkyClinic Wrocław"

Zdjęcia kliniki (wnętrza):
alt="Gabinet zabiegowy SkyClinic Wrocław — nowoczesne wyposażenie, sterylne warunki"
alt="Recepcja kliniki SkyClinic przy ul. Ołtaszyńskiej 71a we Wrocławiu"

Zdjęcia hero zabiegów:
alt="Zabieg SofWave — lifting ultradźwiękowy twarzy bez operacji, klinika SkyClinic"
alt="Przeszczep włosów FUE metodą robota ARTAS — SkyClinic Wrocław"

Zdjęcia na podstronach potrzeb:
alt="Odmładzanie twarzy — lifting bez operacji, skuteczne metody w SkyClinic"

Logo:
alt="SkyClinic — Beginning of Beauty — logo kliniki medycyny estetycznej"
```

### 5.5 Dane strukturalne (Schema.org)

**Na stronie głównej i stronach lokalizacji:**
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

**Na podstronach zabiegów:**
```json
{
  "@context": "https://schema.org",
  "@type": "MedicalProcedure",
  "name": "SofWave",
  "description": "Nieinwazyjny lifting twarzy ultradźwiękami",
  "procedureType": "Noninvasive",
  "bodyLocation": "Twarz"
}
```

**FAQ na podstronach (accordion):**
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [{
    "@type": "Question",
    "name": "Ile trwa efekt zabiegu SofWave?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "Efekty utrzymują się od 12 do 18 miesięcy..."
    }
  }]
}
```

### 5.6 Linki kanoniczne

Każda podstrona zawiera tag canonical w `<head>`:
```html
<link rel="canonical" href="https://skyclinic.pl/zabiegi/sofwave/" />
```

Dotyczy to szczególnie zabiegów wieloobszarowych — każda wersja (twarz/ciało) ma własny canonical wskazujący na siebie samą.

---

## 6. STRUKTURA STRON — SZABLONY

### 6.1 STRONA GŁÓWNA

```
URL:   /
Title: SkyClinic — Klinika Medycyny Estetycznej i Transplantacji Włosów | Wrocław i Warszawa
H1:    Przywracamy pewność siebie

SEKCJA 1 — HERO
Elementy: H1 | subheadline | nawigacja obszarów (6 kafelków) | formularz inline
Kafelki obszarów: Twarz | Ciało | Włosy | Okolice intymne | Laryngologia | Konsultacje
Każdy kafelek = ikona + nazwa + link do /potrzeby/[obszar]/
Formularz: Imię* | Telefon* | Miasto (Wrocław/Warszawa)* | "UMÓW BEZPŁATNĄ KONSULTACJĘ"

SEKCJA 2 — TRUST BAR
4 liczby: "10+ lat doświadczenia" | "67 procedur w ofercie" | "8 specjalizacji" | "2 kliniki"
Tło: #3C3C3C | Tekst: biały

SEKCJA 3 — FILOZOFIA
Overline: "NASZE PODEJŚCIE"
H2: "Tu zaczyna się piękno"
Lead: 2-3 zdania
3 wartości w gridzie: Uczciwość | Profesjonalizm | Rozwój

SEKCJA 4 — PROCES
Overline: "JAK DZIAŁAMY"
H2: "Twoja droga do efektu"
4 kroki: Konsultacja → Edukacja → Zabieg → Opieka pozabiegowa

SEKCJA 5 — POPULARNE POTRZEBY
Overline: "ZACZNIJ OD SWOJEJ POTRZEBY"
H2: "Co Cię do nas sprowadza?"
Grid 3×2: 6 kart potrzeb
Każda karta: zdjęcie + obszar + nazwa potrzeby + "Poznaj metody" → /potrzeby/[obszar]/[slug]/
Sugerowane potrzeby: Odmładzanie twarzy | Przeszczep włosów | Modelowanie sylwetki
                      Poprawa jakości skóry | Leczenie chrapania | Estetyka okolic intymnych

SEKCJA 6 — WYRÓŻNIONE ZABIEGI
Overline: "NASZE SPECJALNOŚCI"
H2: "Zabiegi, z których jesteśmy znani"
5 kart: Przeszczep FUE | Blefaroplastyka | SofWave | Dermapen | Fotona 4D

SEKCJA 7 — NASZ ZESPÓŁ
Overline: "NASZ ZESPÓŁ"
H2: "Lekarze, którym ufają tysiące pacjentów"
Karty: zdjęcie + imię + specjalizacja + CTA
Przycisk: "Poznaj cały zespół" → /o-nas/nasz-zespol/

SEKCJA 8 — OPINIE
Overline: "OPINIE PACJENTÓW"
H2: "Co mówią nasi pacjenci"
Karuzela z gwiazdkami + imieniem + zabiegiem

SEKCJA 9 — DWE KLINIKI
H2: "Dwie kliniki — jedno doświadczenie"
2 kolumny: Wrocław | Warszawa
Każda: zdjęcie + adres + telefon + "Zobacz klinikę" → /o-nas/klinika-[miasto]/

SEKCJA 10 — FORMULARZ
Overline: "KONTAKT"
H2: "Masz pytania? Doradzimy."
Pełny formularz + dane kontaktowe obok
```

### 6.2 STRONA /potrzeby/ (Lista grup)

```
URL:   /potrzeby/
Title: Twoje potrzeby — znajdź zabieg dopasowany do Ciebie | SkyClinic
H1:    Znajdź rozwiązanie dopasowane do Twojej potrzeby

Breadcrumb: Strona główna > Twoje potrzeby

Treść:
- Krótki lead (2-3 zdania)
- 6 dużych kart obszarów: Twarz | Ciało | Włosy | Okolice intymne | Laryngologia | Konsultacje
- Każda karta: zdjęcie obszaru + nazwa + lista 3-4 potrzeb w skrócie + "Przejdź do [obszar]" → /potrzeby/[obszar]/
```

### 6.3 STRONA /potrzeby/[obszar]/ (Lista potrzeb w obszarze)

```
URL:   /potrzeby/twarz/
Title: Zabiegi na twarz — potrzeby i metody leczenia | SkyClinic Wrocław i Warszawa
H1:    Zabiegi na twarz — znajdź metodę dopasowaną do Twojej potrzeby

Breadcrumb: Strona główna > Twoje potrzeby > Twarz

Treść:
- Krótki intro (3-4 zdania o twarzy jako obszarze)
- Grid kart potrzeb (wszystkie potrzeby dla tego obszaru)
- Każda karta: ikona/zdjęcie + nazwa potrzeby + 1 zdanie opisu + "Dowiedz się więcej" → /potrzeby/twarz/[slug-potrzeby]/
```

### 6.4 PODSTRONA POTRZEBY

```
URL:   /potrzeby/twarz/odmładzanie-i-lifting-twarzy/
Title: Odmładzanie i lifting twarzy — skuteczne metody bez operacji | SkyClinic
Meta:  Szukasz naturalnego liftingu twarzy? SkyClinic oferuje SofWave, Fotona, Endermologię i 8 innych metod. Wrocław i Warszawa. Umów bezpłatną konsultację.
H1:    Odmładzanie i lifting twarzy — poznaj skuteczne metody

Breadcrumb: Strona główna > Twoje potrzeby > Twarz > Odmładzanie i lifting twarzy

SEKCJA 1 — HERO
H1 + lead (2 zdania) + sygnał zaufania + CTA "Umów konsultację" + formularz inline

SEKCJA 2 — KIEDY TO DOTYCZY CIEBIE?
H2: "Kiedy to dotyczy Ciebie?"
Lista 4-6 objawów językiem pacjenta (bez medycznego żargonu)

SEKCJA 3 — METODY
H2: "Metody, które stosujemy w SkyClinic"
Karuzela kart zabiegów powiązanych z tą potrzebą
Każda karta: nazwa zabiegu + 1 zdanie + "Sprawdź zabieg →" → /zabiegi/[slug]/

SEKCJA 4 — EFEKTY
H2: "Efekty naszych pacjentów"
Karuzela przed/po (4-8 par)
Alt text: "Efekt [nazwa zabiegu] — [opis] — pacjent SkyClinic"

SEKCJA 5 — FAQ
H2: "Często zadawane pytania o odmładzanie twarzy"
Accordion 4-6 pytań + JSON-LD FAQPage

SEKCJA 6 — CTA
H2: "Masz pytania? Doradzimy."
Telefon + email + formularz kontaktowy
```

### 6.5 PODSTRONA ZABIEGU

```
URL:   /zabiegi/sofwave/
Title: SofWave — nieinwazyjny lifting twarzy ultradźwiękami | SkyClinic Wrocław i Warszawa
Meta:  SofWave to nieinwazyjny lifting twarzy bez igieł i skalpela. Efekt po jednej sesji. Dostępny w SkyClinic Wrocław i Warszawa. Sprawdź ceny i umów konsultację.
H1:    SofWave — nieinwazyjny lifting twarzy ultradźwiękami

Breadcrumb: Strona główna > Zabiegi > SofWave

SEKCJA 1 — HERO
H1 + lead (2-3 zdania) + parametry zabiegu (czas trwania | efekty po | liczba sesji | obszar)
CTA: "UMÓW ZABIEG" (primary) + "CENNIK" (secondary anchor do sekcji cennika)
Formularz inline

SEKCJA 2 — EFEKTY (PRZED/PO)
H2: "Efekty zabiegu SofWave — zdjęcia przed i po"
Karuzela 3-6 par zdjęć z podpisami
Alt: "Efekt zabiegu SofWave — przed i po, wyniki po [X] sesji, SkyClinic"

SEKCJA 3 — OPIS ZABIEGU
H2: "Na czym polega zabieg SofWave?"
Długi tekst SEO (700-1200 słów) + zdjęcia opisowe
Podsekcje H3: "Mechanizm działania" | "Wskazania" | "Przebieg zabiegu" | "Przeciwwskazania"

SEKCJA 4 — WIDEO
H2: "Zabieg SofWave w SkyClinic"
Embed YouTube (jeśli brak — sekcja ukryta)

SEKCJA 5 — CENNIK
H2: "Cennik zabiegu SofWave"
Tabela: Pozycja | Czas trwania | Cena
CTA przy każdej pozycji: "Umów termin"
Nota: "Ceny mają charakter informacyjny. Ostateczna wycena po konsultacji."

SEKCJA 6 — FAQ
H2: "Najczęstsze pytania o SofWave"
Accordion 4-6 pytań + JSON-LD FAQPage

SEKCJA 7 — OPINIE
H2: "Opinie pacjentów po zabiegu SofWave"
3-4 opinie z gwiazdkami

SEKCJA 8 — POWIĄZANE POTRZEBY
H2: "Ten zabieg pomaga przy:"
Kafelki z linkami: "Odmładzanie twarzy" → /potrzeby/twarz/odmładzanie-i-lifting-twarzy/ itd.

SEKCJA 9 — POLECANE ZABIEGI
H2: "Polecane zabiegi"
3 karty powiązanych zabiegów (z tego samego obszaru)

SEKCJA 10 — FORMULARZ
H2: "Zarezerwuj termin"
Pełny formularz kontaktowy
```

### 6.6 KATALOG ZABIEGÓW /zabiegi/

```
URL:   /zabiegi/
Title: Wszystkie zabiegi medycyny estetycznej — katalog | SkyClinic Wrocław i Warszawa
H1:    Katalog zabiegów SkyClinic

Breadcrumb: Strona główna > Zabiegi

Treść:
- Opis klinki (2-3 zdania)
- Filtry: Obszar | Potrzeba | Kategoria
- Grid kart wszystkich zabiegów (67 pozycji)
- Każda karta: nazwa + obszar + potrzeba + "Sprawdź →"
- Domyślne sortowanie: alfabetyczne
```

---

## 7. KATALOG USŁUG — 67 GRUP ZABIEGOWYCH

### 7.1 TWARZ (38 podstron)

| Nazwa zabiegu | Potrzeba | URL slug |
|---|---|---|
| Biorewitalizacja | Jakość skóry i pory | /zabiegi/biorewitalizacja/ |
| Blefaroplastyka | Okolica oczu i powiek | /zabiegi/blefaroplastyka/ |
| Celluma | Jakość skóry i pory | /zabiegi/celluma/ |
| Dermamelan | Przebarwienia i koloryt | /zabiegi/dermamelan/ |
| Dermapen | Jakość skóry i pory | /zabiegi/dermapen/ |
| DyeVL | Przebarwienia i koloryt | /zabiegi/dyevl/ |
| EXION | Odmładzanie i lifting twarzy | /zabiegi/exion/ |
| Endermologia | Odmładzanie i lifting twarzy | /zabiegi/endermologia/ |
| Fotona | Odmładzanie i lifting twarzy | /zabiegi/fotona/ |
| Geneo | Trądzik i oczyszczanie skóry | /zabiegi/geneo/ |
| Hialuronidaza | Owal twarzy i żuchwa | /zabiegi/hialuronidaza/ |
| Innofacial | Trądzik i oczyszczanie skóry | /zabiegi/innofacial/ |
| Karboksyterapia | Jakość skóry i pory | /zabiegi/karboksyterapia/ |
| Komórki macierzyste CGF | Jakość skóry i pory | /zabiegi/komorki-macierzyste-cgf/ |
| Laserowe usuwanie blizn | Blizny | /zabiegi/laserowe-usuwanie-blizn/ |
| Laserowe usuwanie naczynek | Przebarwienia i koloryt | /zabiegi/laserowe-usuwanie-naczynek/ |
| Laseroterapia – odmładzanie | Przebarwienia i koloryt | /zabiegi/laseroterapia-odmładzanie/ |
| Lift całkowity | Odmładzanie i lifting twarzy | /zabiegi/lift-calkowity/ |
| Lift skroniowy | Odmładzanie i lifting twarzy | /zabiegi/lift-skroniowy/ |
| Lifting brwi | Odmładzanie i lifting twarzy | /zabiegi/lifting-brwi/ |
| Lip lift | Usta | /zabiegi/lip-lift/ |
| Lipoliza inekcyjna | Owal twarzy i żuchwa | /zabiegi/lipoliza-inekcyjna/ |
| Lipotransfer | Odmładzanie i lifting twarzy | /zabiegi/lipotransfer/ |
| Lipotransfer Micro Nano Fat | Odmładzanie i lifting twarzy | /zabiegi/lipotransfer-micro-nano-fat/ |
| Mezoterapia igłowa | Jakość skóry i pory | /zabiegi/mezoterapia-iglowa/ |
| Nici liftingujące | Odmładzanie i lifting twarzy | /zabiegi/nici-liftingujace/ |
| Osocze bogatopłytkowe PRP | Jakość skóry i pory | /zabiegi/osocze-bogatoplytkowe-prp/ |
| Otoplastyka | Uszy | /zabiegi/otoplastyka/ |
| Peeling chemiczny | Przebarwienia i koloryt | /zabiegi/peeling-chemiczny/ |
| Powiększanie ust | Usta | /zabiegi/powiekszanie-ust/ |
| SofWave | Odmładzanie i lifting twarzy | /zabiegi/sofwave/ |
| StarWalker | Przebarwienia i koloryt | /zabiegi/starwalker/ |
| Stymulatory tkankowe | Odmładzanie i lifting twarzy | /zabiegi/stymulatory-tkankowe/ |
| Toksyna botulinowa | Zmarszczki mimiczne i botoks | /zabiegi/toksyna-botulinowa/ |
| Usunięcie kuleczek Bichat | Owal twarzy i żuchwa | /zabiegi/usuniecie-kuleczek-bichat/ |
| Wolumetria | Owal twarzy i żuchwa | /zabiegi/wolumetria/ |
| Wypełnienia kwasem hialuronowym | Owal twarzy i żuchwa | /zabiegi/wypelnienia-kwasem-hialuronowym/ |
| Zabiegi pielęgnacyjne | Jakość skóry i pory | /zabiegi/zabiegi-pielegnacyjne/ |

### 7.2 CIAŁO (18 podstron)

| Nazwa zabiegu | Potrzeba | URL slug |
|---|---|---|
| ALMA Spadeep RF | Cellulit i jędrność | /zabiegi/alma-spadeep-rf/ |
| Chirurgiczne usuwanie zmian skórnych | Zmiany skórne i paznokcie | /zabiegi/chirurgiczne-usuwanie-zmian-skornych/ |
| EXION — ciało | Cellulit i jędrność | /zabiegi/exion-cialo/ |
| Endermologia — ciało | Cellulit i jędrność | /zabiegi/endermologia-cialo/ |
| Epilacja laserowa | Trwałe usuwanie owłosienia | /zabiegi/epilacja-laserowa/ |
| Laserowe usuwanie naczynek — ciało | Przebarwienia i koloryt | /zabiegi/laserowe-usuwanie-naczynek-cialo/ |
| Laserowe usuwanie rozstępów | Blizny i rozstępy | /zabiegi/laserowe-usuwanie-rozstepow/ |
| Laseroterapia — ciało | Blizny i rozstępy | /zabiegi/laseroterapia-cialo/ |
| Lipoliza inekcyjna — ciało | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/lipoliza-inekcyjna-cialo/ |
| Liposukcja | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/liposukcja/ |
| Modelowanie pośladków | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/modelowanie-posladkow/ |
| Onda | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/onda/ |
| Plastyka brzucha | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/plastyka-brzucha/ |
| Schwarzy | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/schwarzy/ |
| StarWalker — ciało | Blizny i rozstępy | /zabiegi/starwalker-cialo/ |
| Storz | Cellulit i jędrność | /zabiegi/storz/ |
| Toksyna botulinowa — nadpotliwość | Nadpotliwość | /zabiegi/toksyna-botulinowa-nadpotliwosc/ |
| Zaffiro | Modelowanie sylwetki i redukcja tłuszczu | /zabiegi/zaffiro/ |

### 7.3 WŁOSY (7 podstron)

| Nazwa zabiegu | Potrzeba | URL slug |
|---|---|---|
| Dermapen — skóra głowy | Leczenie wypadania włosów | /zabiegi/dermapen-skora-glowy/ |
| Hair Restoration | Leczenie wypadania włosów | /zabiegi/hair-restoration/ |
| Komórki macierzyste CGF — włosy | Leczenie wypadania włosów | /zabiegi/komorki-macierzyste-cgf-wlosy/ |
| Leczenie łysienia | Leczenie wypadania włosów | /zabiegi/leczenie-lysienia/ |
| Mezoterapia igłowa — skóra głowy | Leczenie wypadania włosów | /zabiegi/mezoterapia-iglowa-skora-glowy/ |
| Osocze bogatopłytkowe PRP — włosy | Leczenie wypadania włosów | /zabiegi/osocze-bogatoplytkowe-prp-wlosy/ |
| Przeszczep włosów FUE | Przeszczep włosów i zarostu | /zabiegi/przeszczep-wlosow-fue/ |

### 7.4 OKOLICE INTYMNE (9 podstron)

| Nazwa zabiegu | Potrzeba | URL slug |
|---|---|---|
| Labioplastyka | Zabiegi chirurgiczne okolic intymnych | /zabiegi/labioplastyka/ |
| Laserowe leczenie NTM | Komfort i funkcja | /zabiegi/laserowe-leczenie-ntm/ |
| Laserowe wybielanie okolic intymnych | Estetyka okolic intymnych | /zabiegi/laserowe-wybielanie-okolic-intymnych/ |
| Leczenie atrofii i świądu pochwy | Komfort i funkcja | /zabiegi/leczenie-atrofii-i-swiadu-pochwy/ |
| Rewitalizacja laserowa pochwy | Komfort i funkcja | /zabiegi/rewitalizacja-laserowa-pochwy/ |
| Rewitalizacja pochwy | Komfort i funkcja | /zabiegi/rewitalizacja-pochwy/ |
| Rewitalizacja pochwy PRP | Komfort i funkcja | /zabiegi/rewitalizacja-pochwy-prp/ |
| Rewitalizacja warg sromowych | Estetyka okolic intymnych | /zabiegi/rewitalizacja-warg-sromowych/ |
| Wypełnienie punktu G | Estetyka okolic intymnych | /zabiegi/wypelnienie-punktu-g/ |

### 7.5 LARYNGOLOGIA (4 podstrony)

| Nazwa zabiegu | Potrzeba | URL slug |
|---|---|---|
| Ewaporyzacja krypt migdałków | Migdałki i nieprzyjemny zapach z ust | /zabiegi/ewaporyzacja-krypt-migdalkow/ |
| Laserowe leczenie chrapania | Leczenie chrapania | /zabiegi/laserowe-leczenie-chrapania/ |
| Laserowe podcięcie wędzidełka | Leczenie chrapania | /zabiegi/laserowe-podciecie-wedzidelka/ |
| Leczenie krwawienia z nosa | Leczenie chrapania | /zabiegi/leczenie-krwawienia-z-nosa/ |

---

## 8. KOMPONENTY GLOBALNE

### 8.1 HEADER

- Wysokość: 72px desktop / 60px mobile
- Logo: wersja pozioma po lewej
- Sticky: tak (zmniejsza się przy scrollu + box-shadow)
- Mobile: hamburger (☰) → drawer (slide-in z lewej)

### 8.2 FOOTER

```
4 kolumny:
1. Logo + "Beginning of Beauty" + social icons (FB, IG, TikTok, LinkedIn)
2. Zabiegi: 6-8 linków do popularnych zabiegów
3. O nas: Klinika Wrocław | Klinika Warszawa | Nasz zespół | Opinie | Kariera
4. Kontakt: Wrocław: adres + tel | Warszawa: adres + tel

Dół:
© 2024 SkyClinic Sp. z o.o. | Polityka prywatności | Regulamin | Cookies

Tło: #3C3C3C | Tekst: #FFFFFF | Linki: #C0C0C0 (hover: #FFFFFF)
```

### 8.3 FORMULARZ INLINE (skrócony)

```
Pola:    Imię i nazwisko* | Numer telefonu* | Miasto* [Wrocław / Warszawa]
Przycisk: "UMÓW BEZPŁATNĄ KONSULTACJĘ"
Zgoda:   "Wyrażam zgodę na przetwarzanie danych osobowych zgodnie z polityką prywatności." (required)
Sukces:  "Dziękujemy! Oddzwonimy w ciągu 24 godzin roboczych."
Błąd:    "Coś poszło nie tak. Spróbuj ponownie lub zadzwoń do nas."
```

### 8.4 FORMULARZ PEŁNY

```
Pola:     Imię i nazwisko* | Numer telefonu* | Adres e-mail | 
          Czego dotyczy zapytanie? (dropdown: lista obszarów) |
          Treść wiadomości (opcjonalne) |
          Preferowana lokalizacja* [Wrocław / Warszawa / Dowolna]
Przyciski: "WYŚLIJ WIADOMOŚĆ"
Zgody:    RODO (required) | Marketing (opcjonalne)
Sukces:   "Wiadomość wysłana! Odezwiemy się w ciągu 24 godzin."
```

### 8.5 COOKIE BANNER

```
Tekst:   "Ta strona używa plików cookie, aby zapewnić najlepszą jakość usług. Korzystając ze strony, zgadzasz się na ich użycie."
Przyciski: "Akceptuję wszystkie" (primary) | "Dostosuj ustawienia" (secondary) | "Odrzuć opcjonalne" (link)
```

---

## 9. WYMAGANIA TECHNICZNE

### 9.1 SEO

- Unikalny `<title>` + `<meta name="description">` na każdej podstronie
- Dokładnie jeden `<h1>` na podstronę
- Alt text na wszystkich zdjęciach (patrz sekcja 5.4)
- Breadcrumbs widoczne + JSON-LD BreadcrumbList
- JSON-LD: MedicalClinic, MedicalProcedure, FAQPage
- Canonical URL na każdej podstronie
- sitemap.xml (automatycznie generowany)
- robots.txt

### 9.2 Performance

- Core Web Vitals: LCP < 2.5s, CLS < 0.1, FID < 100ms
- Lazy loading wszystkich zdjęć (poza hero LCP)
- Format zdjęć: WebP z fallback JPG
- Google Fonts: preload Montserrat (400, 500, 600, 700)
- Minifikacja CSS i JS

### 9.3 Dostępność (WCAG 2.1 AA)

- Kontrast minimum 4.5:1 (tekst) i 3:1 (UI)
- Focus visible na wszystkich elementach interaktywnych
- Semantyczny HTML: nav, main, section, article, footer
- aria-labels na przyciskach ikonowych
- Skip-to-main-content link

### 9.4 RODO i prawo medyczne

- Cookie consent (wymagany przed załadowaniem analityki)
- Polityka prywatności: /polityka-prywatnosci/
- Regulamin: /regulamin/
- Nota medyczna na każdej podstronie zabiegu: "Treści zawarte na tej stronie mają charakter informacyjny i nie stanowią porady medycznej. Skonsultuj się z lekarzem."
- Zdjęcia przed/po: zarządzane po stronie kliniki (zgody pacjentów)

### 9.5 Mobile

- Breakpoints: 375px | 768px | 1024px | 1280px
- Mobile-first CSS
- Touch targets: min. 44×44px
- Karuzele: swipe-friendly

---

## 10. DANE DO DOSTARCZENIA PRZEZ KLINIKĘ

- [ ] Logo SVG (pionowe + poziome) — biały i ciemnoszary wariant
- [ ] Zdjęcia lekarzy (portretowe, białe tło lub klinika)
- [ ] Zdjęcia wnętrz obu klinik
- [ ] Zdjęcia hero dla każdego zabiegu (min. 1/zabieg)
- [ ] Zdjęcia przed/po (min. 2 pary/zabieg, z zgodami pacjentów)
- [ ] Adresy obu klinik + telefony + emaile
- [ ] Godziny otwarcia
- [ ] Cennik (pozycje z cenami lub zakresami)
- [ ] Biografie lekarzy
- [ ] Opinie pacjentów (min. 20, źródło: Google/Znany Lekarz)
- [ ] Social media links
- [ ] Dane do polityki prywatności i regulaminu

---

## 11. PLAN WDROŻENIA

### Etap 1 — Treści (przed Lovable)
1. Generowanie tekstów dla wszystkich 67 podstron zabiegów
2. Generowanie tekstów dla 24 podstron potrzeb
3. Weryfikacja treści przez lekarzy kliniki

### Etap 2 — Fundament w Lovable
4. Konfiguracja projektu, design tokens (kolory, czcionki)
5. Komponenty bazowe: przyciski, karty, formularze
6. Header + Footer + layout wrapper

### Etap 3 — Szablony stron
7. Homepage
8. Template: /potrzeby/ i /potrzeby/[obszar]/
9. Template: podstrona potrzeby
10. Template: podstrona zabiegu
11. Template: katalog /zabiegi/
12. Strony O nas i kontakt

### Etap 4 — Content i połączenia
13. Wdrożenie 67 podstron zabiegowych z treściami
14. Wdrożenie 24 podstron potrzeb z linkowaniem many-to-many
15. Wdrożenie sekcji /potrzeby/ z obszarami
16. Podstrony klinik + zespołu

### Etap 5 — SEO i optymalizacja
17. Meta tagi dla wszystkich podstron
18. JSON-LD struktury danych
19. Sitemap + robots.txt
20. Performance audit
21. WCAG audit
22. Testy cross-browser

### Etap 6 — Uruchomienie
23. Staging → review klienta → produkcja

---

*Dokument: SkyClinic_Specyfikacja_Strony_v1.1*  
*Data: marzec 2026*  
*Zmiany względem v1.0: architektura /potrzeby/, megamenu, SEO, URL, teksty PL, many-to-many*
