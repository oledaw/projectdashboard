# IT Portfolio — Decision Dashboard

> Narzędzie do zarządzania portfolio projektów IT oparte na świadomych decyzjach,
> a nie na intuicji. Każdy element przechodzi przez trzy pytania:
> **Dlaczego to robimy? Ile to kosztuje? Co zyskujemy?**

---

## Spis treści

- [Filozofia](#filozofia)
- [Kategorie projektów](#kategorie-projektów)
- [Ocena Impact i Effort](#ocena-impact-i-effort)
- [Priorytet — wyliczany automatycznie](#priorytet--wyliczany-automatycznie)
- [Status — zarządzany przez akcje](#status--zarządzany-przez-akcje)
- [Postęp — z zadań w epikach](#postęp--z-zadań-w-epikach)
- [Workflow tworzenia elementu](#workflow-tworzenia-elementu)
- [Workflow zarządzania otwartym projektem](#workflow-zarządzania-otwartym-projektem)
- [Impact Matrix](#impact-matrix)
- [Test CFO](#test-cfo)
- [Happy Path](#happy-path)
- [Widoki](#widoki)
- [Zasady portfolio](#zasady-portfolio)
- [Słownik pojęć](#słownik-pojęć)

---

## Filozofia

Dashboard wymusza **świadome uzasadnienie każdej inicjatywy** zanim trafi do portfolio.
Trzy zasady prowadzące projekt przez cały cykl życia:

1. **Zdefiniuj** — do której kategorii należy inicjatywa i jakie ma uzasadnienie biznesowe
2. **Oceń** — jak duży jest impact i ile kosztuje realizacja (opisowo, bez arbitralnych cyfr)
3. **Działaj** — opisz ścieżkę sukcesu, dodaj zadania, śledź postęp

> **Reguła CFO:** Każdy element portfolio musi przejść test jednego zdania.
> Jeśli nie potrafisz go obronić jednym zdaniem — element nie powinien być w portfolio.

---

## Kategorie projektów

Kategoria określa **uzasadnienie biznesowe** inicjatywy. Nie można jej zmienić po zapisaniu
— zmiana uzasadnienia oznacza de facto nowy projekt.

### 🔵 Required

**Definicja:** Musimy to zrobić. Istnieje zewnętrzna lub kontraktowa zależność,
bez której nie możemy działać lub narażamy się na poważne konsekwencje.

**Test CFO:** *„Bo musimy — wymaga tego [partner / klient / regulacja]."*

**Pola obowiązkowe:**
- Kto wymaga — podmiot zewnętrzny egzekwujący wymaganie
- Deadline — termin wynikający ze zobowiązania zewnętrznego
- Co się stanie jeśli nie zrobimy — konkretna konsekwencja (utrata kontraktu, blokada integracji, kara)

**Przykłady:** SSO z Azure AD jako warunek podpisania kontraktu,
pole API wymagane przez integrację partnera, wymóg zgodności z DORA/RODO.

---

### 🟡 Optimization

**Definicja:** Robimy to samo taniej, szybciej lub z mniejszym ryzykiem błędu.
Istnieje **mierzalna oszczędność** — godziny pracy, koszty operacyjne, eliminacja błędów.

**Test CFO:** *„Oszczędzamy [X h/mies. lub Y PLN/mies.] na [obszarze]."*

**Pola obowiązkowe:**
- Oszczędność — konkretna liczba (h/mies. lub PLN/mies.)
- Obszar — dział lub proces, który zyskuje
- Jak wygląda problem dziś — opis aktualnego stanu, który chcemy zmienić

**Ważne — atomowość:** Optymalizacja powinna dotykać jednego obszaru systemu.
Jeśli zmiana wymaga modyfikacji wielu modułów — to sygnał do decyzji architektonicznej
i potencjalnego podniesienia do osobnego projektu.

**Przykłady:** Automatyzacja obiegu faktur, nowe pole API eliminujące ręczne przeliczenia w CRM.

---

### 🟢 Growth

**Definicja:** Zarobimy więcej lub zwiększymy kluczową metrykę biznesową.
**Wymagane są dane** potwierdzające istnienie problemu lub szansy — bez nich
inicjatywa spada do kategorii Enhancement.

**Test CFO:** *„Zwiększymy [metrykę] o [efekt]. Wiemy to bo [dowód]. Testujemy przez [sposób]."*

**Pola obowiązkowe:**
- Metryka sukcesu — co mierzymy (konwersja, przychód, retencja, liczba użytkowników)
- Oczekiwany efekt — konkretna liczba lub przedział (+5%, +3–4pp)
- Sposób testu / MVP — jak weryfikujemy hipotezę przed pełnym wdrożeniem
- Dowód że problem istnieje — dane jakościowe lub ilościowe (drop-off w lejku, feedback użytkowników z liczbami)

**Przykłady:** Redesign strony rezerwacji oparty o analizę drop-off 38% w kroku 2 lejka,
integracja z bikesharing potwierdzająca popyt pilotażem w jednym mieście.

---

### ⚪ Enhancement

**Definicja:** Nice-to-have. Brak twardych danych uzasadniających realizację.
Inicjatywa może być wartościowa, ale **nie wiemy tego z danych** — tylko z intuicji,
estetyki lub pojedynczego feedback.

**Test CFO:** *„Nie mamy twardych danych. CFO nie zaakceptuje bez pomiaru."*

**Pola obowiązkowe:**
- Uzasadnienie — opis źródła pomysłu (nawet subiektywnego)
- Co zmierzyć żeby awansować do Growth — konkretny eksperyment lub pomiar,
  który pozwoli reklasyfikować inicjatywę na Growth

**Zasada awansu:** Enhancement z twardymi danymi → reklasyfikuj jako Growth.
Enhancement nigdy nie powinien trafić do realizacji bez walidacji.

**Przykłady:** Odświeżenie UI „bo wygląda staro", marketplace partnerów bez potwierdzenia popytu.

---

## Ocena Impact i Effort

Ocena zastępuje arbitralne skale liczbowe **opisowymi opcjami** dopasowanymi do kategorii.
Każda opcja ma ukrytą wartość numeryczną używaną wyłącznie do pozycjonowania na Impact Matrix
i obliczania priorytetu. Użytkownik nigdy nie wprowadza cyfr ręcznie.

### Impact — zależny od kategorii

Każda kategoria ma własne 3 opcje opisujące **skalę efektu biznesowego**:

| Kategoria | Opcja 1 (wysoki) | Opcja 2 (średni) | Opcja 3 (niski) |
|---|---|---|---|
| **Required** | Blokuje partnera / launch `88` | Ważne, ale jest obejście `62` | Formalność, niskie ryzyko `35` |
| **Optimization** | Mierzalna oszczędność `72` | Szacunkowa oszczędność `50` | Marginalny / niepewny `28` |
| **Growth** | Potwierdzony potencjał `78` | Hipoteza z sygnałem `52` | Zakład rynkowy `32` |
| **Enhancement** | Realna uciążliwość dla użytkowników `45` | Dopracowanie i spójność `28` | Niepewny — brak walidacji `15` |

> Liczby w backtickach to wartości wewnętrzne (`0–100`) używane do obliczeń.

### Effort — wspólny dla wszystkich kategorii

Nakład oceniany jest przez pryzmat **złożoności i czasu**, nie osobodni:

| Opcja | Opis | Wartość wewnętrzna |
|---|---|---|
| **Szybka zmiana — 1–2 tygodnie** | Atomowa, izolowana zmiana. Jeden moduł, jedno zadanie. Małe ryzyko. | `15` |
| **Projekt — kilka tygodni** | Kilka komponentów, integracja lub testy. Wymaga planowania sprintu. | `48` |
| **Duży projekt — wiele tygodni / miesięcy** | Wiele modułów lub integracji zewnętrznych. Wymaga decyzji architektonicznej. | `82` |

---

## Priorytet — wyliczany automatycznie

Priorytet **nie jest polem do wypełnienia**. Wynika ze wzoru opartego na ocenie impact i effort:

```
score = impact × 0.6 + (100 − effort) × 0.4
```

| Score | Priorytet |
|---|---|
| ≥ 75 | 🔴 Krytyczny |
| ≥ 55 | 🟡 Wysoki |
| ≥ 35 | 🔵 Średni |
| < 35 | ⚪ Niski |

**Uzasadnienie wag:** Impact ma wyższy współczynnik (0.6) bo skala efektu biznesowego
jest ważniejsza niż koszt realizacji. Effort jest odwrócony — niski nakład podnosi priorytet,
wysoki go obniża. Inicjatywy o wysokim impact i niskim effort mają najwyższy priorytet.

**Przykłady:**

| Projekt | Impact | Effort | Score | Priorytet |
|---|---|---|---|---|
| SSO z Azure AD | 88 | 48 | 88×0.6 + 52×0.4 = **74** | Wysoki |
| Nowe pole API (wymaganie partnera) | 88 | 15 | 88×0.6 + 85×0.4 = **87** | Krytyczny |
| Odświeżenie UI (brak danych) | 15 | 48 | 15×0.6 + 52×0.4 = **30** | Niski |

---

## Status — zarządzany przez akcje

Status **nie jest polem formularza** ani edytora. Jest pochodną stanu zadań i decyzji
podjętych przez akcje w panelu projektu.

### Logika wyliczania statusu

```
jeśli manualStatus = 'blocked'  → Zablokowany  (sticky — tylko ręczne odblokowanie)
jeśli manualStatus = 'done'     → Gotowe        (nadpisane ręcznie)
jeśli brak zadań                → Planowany
jeśli wszystkie zadania = done  → Gotowe        (automatycznie)
jeśli jakiekolwiek zadanie      → W toku
```

### Dostępne akcje statusu w panelu

| Aktualny status | Dostępne akcje |
|---|---|
| **Planowany** | ▶ Rozpocznij |
| **W toku** | ✓ Zamknij jako gotowe · ⚠ Zablokuj |
| **Zablokowany** | ↩ Odblokuj |
| **Gotowe** | ↩ Wznów |

> **Uwaga:** „Zablokuj" ustawia `manualStatus = 'blocked'` który nadpisuje logikę automatyczną.
> Odblokowanie czyści `manualStatus` — status wraca do wyliczanego ze stanu zadań.

### Kiedy używać blokady

Blokada (`Zablokowany`) sygnalizuje **zewnętrzną przeszkodę** poza kontrolą zespołu:
- odkrycie nieatomowości projektu wymagające decyzji architektonicznej
- oczekiwanie na decyzję zewnętrzną (klient, partner, regulacja)
- zablokowanie przez inną inicjatywę (dependency)

Zablokowany projekt powinien mieć opisany powód w sekcji komentarzy.

---

## Postęp — z zadań w epikach

Postęp **nie jest polem do wpisania**. Jest liczony automatycznie:

```
postęp = (liczba zadań ukończonych / wszystkie zadania) × 100
```

### Struktura: Projekt → Epiki → Zadania

```
Projekt (np. SSO z Azure AD)
├── Epik: SAML flow
│   ├── ☑ Konfiguracja SP metadata
│   ├── ☐ Implementacja SP-initiated SSO
│   └── ☐ Testy z tenant testowym klienta
└── Epik: Mapowanie ról
    ├── ☐ Mapping grup Azure AD → role systemowe
    ├── ☐ Testy uprawnień dla każdej roli
    └── ☐ Dokumentacja procesu dla klienta
```

**Epik** = logiczna grupa powiązanych zadań. Powinien reprezentować jeden obszar dostarczany
niezależnie (np. backend, frontend, testy, dokumentacja).

**Zadanie** = atomowa jednostka pracy z checkboxem. Po zaznaczeniu wszystkich zadań
status projektu automatycznie przechodzi na `Gotowe`.

### Jak zarządzać epikami i zadaniami

1. Otwórz panel projektu
2. W sekcji **„Epiki i zadania"** wpisz nazwę epiku → kliknij `+ Epik`
3. Rozwiń epik → wpisz nazwę zadania → kliknij `+ Zadanie` lub naciśnij `Enter`
4. Zaznaczaj zadania jako ukończone klikając checkbox
5. Postęp i status aktualizują się natychmiast

---

## Workflow tworzenia elementu

Nowy element portfolio przechodzi przez **3-krokowy wizard**:

### Krok 1 — Zdefiniuj

- Wybór kategorii (Required / Optimization / Growth / Enhancement)
- Nazwa projektu i właściciel
- Opis / kontekst biznesowy
- Pola specyficzne dla kategorii

> Po wyborze kategorii pojawiają się pola dopasowane do jej logiki.
> Nie ma pól „opcjonalnych" bez znaczenia — każde pole jest pytaniem wymuszającym myślenie.

### Krok 2 — Oceń

- Wybór opcji impact (3 opisowe opcje dopasowane do kategorii)
- Wybór opcji effort (3 opisowe opcje wspólne dla wszystkich kategorii)
- Live preview pozycji na Impact Matrix
- Wyliczony priorytet wyświetlany w podglądzie
- Podgląd testu CFO aktualizowany na bieżąco

> Na tym etapie nie wpisuje się żadnych liczb — tylko wybiera opis pasujący do sytuacji.

### Krok 3 — Działaj

- Opis Happy Path (sekwencja kroków ścieżki sukcesu)
- Informacja o tym co jest zarządzane automatycznie (status, postęp, priorytet)

> Po zapisaniu projekt trafia do portfolio ze statusem `Planowany`.
> Zadania i epiki dodaje się w panelu projektu.

---

## Workflow zarządzania otwartym projektem

### Panel projektu zawiera

| Sekcja | Opis |
|---|---|
| **Badges** | Klucz projektu · Kategoria · Status (aktualny, wyliczony) |
| **Akcje** | Edytuj · zmiana statusu · Archiwizuj |
| **Assess cards** | Impact · Effort · Priorytet (wyliczony) |
| **Meta** | Pola specyficzne dla kategorii |
| **Test CFO** | Zdanie obrony projektu |
| **Opis** | Kontekst i tło decyzji |
| **Happy Path** | Sekwencja kroków ścieżki sukcesu |
| **Postęp** | Pasek z % i licznikiem zadań |
| **Epiki i zadania** | Zarządzanie zadaniami, checkboxy |
| **Komentarz** | Notatki decyzyjne |

### Edycja projektu

Przycisk **„✏ Edytuj"** otwiera drawer z pełnym zestawem pól:

- Nazwa, właściciel, opis
- Pola specyficzne dla kategorii
- Zmiana oceny impact (→ przeliczy priorytet i pozycję na matrycy)
- Zmiana oceny effort (→ przeliczy priorytet i pozycję na matrycy)
- Happy Path

> Status, postęp i priorytet **nie są polami edycji** — są pochodnymi innych danych.

---

## Impact Matrix

Dwuwymiarowa macierz decyzyjna pozycjonująca projekty według:

- **Oś X (pozioma):** Effort — nakład pracy (lewo = niski, prawo = wysoki)
- **Oś Y (pionowa):** Impact — efekt biznesowy (góra = wysoki, dół = niski)

### Kwadranty

| Kwadrant | Pozycja | Interpretacja |
|---|---|---|
| **Rób natychmiast** | Wysoki impact, wysoki effort | Priorytet strategiczny — warto mimo kosztów |
| **Rozważ** | Wysoki impact, niski effort | Quick win — zacznij od tych |
| **Planuj** | Niski impact, wysoki effort | Wróć kiedy będziesz mieć zasoby |
| **Unikaj** | Niski impact, niski effort | Nawet jeśli łatwe — nie warto |

### Jak czytać macierz

Pozycja każdego projektu wynika bezpośrednio z **wartości wewnętrznych** wybranych opcji
impact i effort — nie z ręcznego pozycjonowania. Zmiana oceny w edytorze natychmiast
przesuwa projekt na macierzy.

Kolor kropki odpowiada kategorii projektu:
- 🔵 Niebieski — Required
- 🟡 Żółty — Optimization
- 🟢 Zielony — Growth
- ⚫ Szary — Enhancement

---

## Test CFO

Każdy projekt musi być obroniony **jednym zdaniem** zrozumiałym dla osoby decyzyjnej
nieznającej szczegółów technicznych.

### Szablony per kategoria

**Required:**
> *„Musimy — wymaga tego [partner/klient/regulacja]. Bez tego: [konkretna konsekwencja]."*

**Optimization:**
> *„Oszczędzamy [X h/mies. lub Y PLN/mies.] miesięcznie na [obszarze]."*

**Growth:**
> *„Zwiększymy [metrykę] o [efekt]. Mamy dane: [dowód]. Testujemy przez [sposób]."*

**Enhancement:**
> *„Brak twardych danych. CFO nie zaakceptuje bez pomiaru."*

> Enhancement nigdy nie powinien trafić do realizacji z ostatnim zdaniem testu CFO.
> To sygnał do zatrzymania i zebrania danych.

---

## Happy Path

Happy Path to **sekwencja kroków opisująca ścieżkę sukcesu** — co dzieje się gdy
wszystko idzie zgodnie z planem, od pierwszego triggera do ostatecznego rezultatu.

### Po co Happy Path w portfolio

- Wymusza myślenie o końcowym efekcie zanim zacznie się implementacja
- Pomaga wykryć brakujące zależności (np. „kto wysyła potwierdzenie?")
- Stanowi podstawę do rozbicia na epiki i zadania
- Ułatwia komunikację z interesariuszami bez żargonu technicznego

### Jak pisać dobry Happy Path

1. Zacznij od **triggera** — co wywołuje akcję (użytkownik klika, system odbiera, faktura wpływa)
2. Każdy krok = **jedna akcja lub decyzja**
3. Opisuj **co się dzieje**, nie **jak jest zaimplementowane**
4. Kończ na **konkretnym rezultacie** (użytkownik widzi potwierdzenie, dane trafiają do ERP)
5. Minimum 3, maksimum 8 kroków — więcej oznacza zbyt złożony scope

### Przykład (dobry)

```
1. Partner wysyła request z AllowForInternationalVisits: true
2. API waliduje flagę i tworzy wizytę z oznaczeniem międzynarodowym
3. System zwraca potwierdzenie z nowym identyfikatorem
4. Partner integruje odpowiedź i wyświetla wizytę użytkownikowi
```

### Przykład (zły — zbyt techniczny)

```
1. POST /api/v2/visits z payload {allowIntl: true}
2. Middleware waliduje JWT token i sprawdza uprawnienia
3. Service layer wywołuje VisitRepository.create()
4. Baza danych zapisuje rekord z flagą allow_international = 1
```

---

## Widoki

### Lista

Tabela grupowana według kategorii. Pokazuje:
- Status (wyliczony)
- Postęp (wyliczony z zadań)
- Priorytet (wyliczony ze wzoru)
- Właściciel (inicjały)

Filtry pozwalają zawęzić widok do kategorii, statusu lub blokad.

### Pipeline decyzji (Kanban)

4 kolumny odpowiadające statusom: Planowane · W realizacji · Zablokowane · Gotowe.
Każda karta pokazuje kategorię i wyliczony priorytet.

### Impact Matrix

Dwuwymiarowa macierz z kropkami reprezentującymi projekty.
Pozycja wynika z oceny impact i effort — nie z ręcznego ustawiania.

---

## Zasady portfolio

### Balans kategorii

Zdrowe portfolio IT powinno zachowywać proporcje:

| Kategoria | Sugerowany udział | Ryzyko przy przekroczeniu |
|---|---|---|
| Required | 15–25% | Zbyt dużo = dług techniczny lub słaba architektura |
| Optimization | 20–35% | Zbyt mało = rosnące koszty operacyjne |
| Growth | 25–40% | Zbyt mało = stagnacja biznesowa |
| Enhancement | max 15% | Zbyt dużo = brak dyscypliny decyzyjnej |

### Reguła atomowości (Optimization)

Projekt optymalizacyjny powinien dotykać **jednego obszaru systemu**.
Jeśli w trakcie analizy okazuje się że zmiana wymaga modyfikacji wielu modułów:

1. Zatrzymaj projekt
2. Ustaw status `Zablokowany`
3. Opisz problem w komentarzu
4. Przeprowadź decyzję architektoniczną (ADR)
5. Rozważ podział na mniejsze atomowe projekty

### Reguła walidacji (Enhancement)

Żaden Enhancement nie powinien wchodzić do realizacji bez:
- zdefiniowanego eksperymentu walidacyjnego (landing page, heatmapa, user interviews)
- progu awansu do Growth (np. „≥20 zapisów", „satisfaction score <60%")

### Reguła danych (Growth)

Projekt Growth bez danych potwierdzających istnienie problemu lub szansy
powinien zostać **reklasyfikowany do Enhancement** do czasu zebrania dowodów.

---

## Słownik pojęć

| Pojęcie | Definicja |
|---|---|
| **Impact** | Efekt biznesowy realizacji projektu — skala korzyści lub konsekwencji braku działania |
| **Effort** | Nakład pracy i złożoność realizacji — czas, liczba modułów, ryzyko integracji |
| **Priorytet** | Wyliczony score: `impact × 0.6 + (100 − effort) × 0.4` — nie pole ręczne |
| **Status** | Pochodna stanu zadań i akcji w panelu — nie pole ręczne ani formularza |
| **Postęp** | Procent ukończonych zadań we wszystkich epikach projektu |
| **Epik** | Logiczna grupa zadań reprezentująca jeden obszar dostarczany niezależnie |
| **Zadanie** | Atomowa jednostka pracy z checkboxem (done / not done) |
| **Happy Path** | Sekwencja kroków opisująca ścieżkę sukcesu od triggera do rezultatu |
| **Test CFO** | Zdanie obronny projekt zrozumiałe dla osoby decyzyjnej bez wiedzy technicznej |
| **Atomowość** | Właściwość zmiany dotykającej jednego izolowanego obszaru systemu |
| **manualStatus** | Wewnętrzna flaga umożliwiająca ręczne nadpisanie statusu (`blocked` / `done` / `null`) |
| **Impact Matrix** | Macierz 2D pozycjonująca projekty według impact (Y) i effort (X) |
| **Reklasyfikacja** | Zmiana kategorii projektu gdy zebranie danych zmienia uzasadnienie biznesowe |
| **ADR** | Architecture Decision Record — dokument opisujący decyzję architektoniczną i jej uzasadnienie |

---

*Ostatnia aktualizacja: Maj 2026*
