# FastFrameFito — Arenaria

Mobilna aplikacja webowa do terenowego wykonywania zdjęć fitosocjologicznych. Działa jako PWA (Progressive Web App) — instaluje się na ekranie głównym telefonu i działa jak natywna aplikacja, bez potrzeby instalacji ze sklepu.

> Zaprojektowana z myślą o pracy w terenie: szybka, prosta w obsłudze, działa offline.

---

## Instalacja na telefonie

**Android (Chrome):**
1. Otwórz adres aplikacji w Chrome
2. Kliknij ⋮ → *Dodaj do ekranu głównego*

**iPhone (Safari):**
1. Otwórz adres aplikacji w Safari
2. Kliknij ikonę udostępniania □↑ → *Dodaj do ekranu głównego*

---

## Funkcje

### 🔍 Szukaj
Panel wyszukiwania gatunków i dodawania ich do bieżącego zdjęcia.

- **Wyszukiwanie tekstowe** — wpisz min. 2 znaki: akronim 8-znakowy, nazwę łacińską lub polską. Wyniki pojawiają się na bieżąco.
- **Filtr grup** — przyciski *Wszystkie / Naczyniowe / Mszaki / Porosty* zawężają pulę wyszukiwania.
- **Rozpoznawanie głosowe 🎤** — przycisk mikrofonu umożliwia dyktowanie nazwy gatunku (Chrome na Androidzie). Wystarczy powiedzieć np. *„Pinus sylvestris"*.
- **Popup warstwy** — po wybraniu gatunku pojawia się okienko z wyborem warstwy roślinności (A/B/C/D). Jeden gatunek może być dodany do wielu warstw jednocześnie.
- **Wskaźnik warstw** — przy gatunkach już dodanych widoczna jest informacja o zajętych warstwach, np. `[AC]`.

### 📋 Zdjęcie
Panel bieżącego zdjęcia fitosocjologicznego z pełną główką.

#### Główka zdjęcia
- **GPS 📍** — automatyczne pobranie współrzędnych WGS84 (stopnie dziesiętne)
- **Nr zdjęcia / stanowisko** — pole tekstowe do 60 znaków
- **Autor** i **Data**
- **Powierzchnia** zdjęcia (m²)
- **Ekspozycja** (N, NE, E, SE, S, SW, W, NW, płaski)
- **Nachylenie** (°)
- **Zwarcie warstw** A, B, C, D (%)
- **Wysokość warstw** A i B (m)
- **Uwagi** — pole tekstowe do 120 znaków

#### Tabela gatunków
Gatunki posortowane warstwami A→B→C→D, a w obrębie warstwy alfabetycznie. Kolumny: grupa (NAC/MSZ/POR), nazwa łacińska, nazwa polska, ochrona, warstwa, skala BB.

#### Skala ilościowości Braun-Blanquet
| Wartość | Znaczenie |
|---------|-----------|
| `5` | pokrycie >75% |
| `4` | pokrycie 50–75% |
| `3` | pokrycie 25–50% |
| `2` | pokrycie 5–25% |
| `1` | pokrycie <5%, liczny |
| `+` | nieliczny, małe pokrycie |
| `r` | pojedyncze okazy |

#### Warstwy roślinności
| Warstwa | Opis |
|---------|------|
| `A` | Warstwa drzew |
| `B` | Warstwa podszytu |
| `C` | Warstwa runa |
| `D` | Warstwa mszysta |

#### Przyciski akcji
- **💾 Zapisz** — zapisuje bieżące zdjęcie do archiwum (lub aktualizuje istniejące)
- **Wyczyść** — usuwa wszystkie gatunki z bieżącego zdjęcia
- **⬇ Eksport** — eksportuje bieżące zdjęcie (CSV lista lub format BB)
- **✉ Mail** — wysyła bieżące zdjęcie mailem

### 📚 Archiwum
Panel zarządzania zapisanymi zdjęciami.

- **Lista zdjęć** — każde zdjęcie z nazwą/nr stanowiska, datą i liczbą gatunków
- **Zaznaczanie** — checkbox przy każdym zdjęciu; przycisk *Zaznacz wszystkie*
- **Otwórz** — wczytuje zdjęcie do edycji w panelu Zdjęcie
- **＋ Nowe zdjęcie** — czyści bieżące zdjęcie i zaczyna nowe

#### Eksport wielu zdjęć
- **⬇ CSV listy** — każde zaznaczone zdjęcie z pełną główką jako komentarze `#`, sklejone w jeden plik
- **⬇ Tabela BB** — klasyczny format fitosocjologiczny: gatunki i warstwy w wierszach, zdjęcia w kolumnach (kompatybilny z JUICE i TurboVeg). Metadane główek jako wiersze nagłówkowe.
- **✉ Wyślij** — zaznaczone zdjęcia w treści maila
- **🗑 Usuń** — trwale usuwa zaznaczone zdjęcia z archiwum

### 🗄 Baza
Panel zarządzania wbudowaną bazą gatunków.

- **Stan bazy** — liczba gatunków w grupach: naczyniowe, mszaki, porosty
- **⬇ Eksport CSV** — pobiera całą bazę do pliku CSV
- **✉ Wyślij bazę** — wysyła bazę mailem
- **⬆ Importuj CSV** — scala zaimportowany plik z istniejącą bazą (nowe rekordy dodawane, istniejące aktualizowane)

---

## Format akronimów

Akronimy 8-znakowe: **pierwsze 4 litery rodzaju + pierwsze 4 litery epitetu**, np.:
- *Pinus sylvestris* → `Pinusylv`
- *Abies alba* → `Abiealba`
- *Vaccinium myrtillus* → `Vaccmyrt`

Format zgodny ze schematem stosowanym w JUICE i TurboVeg, co ułatwia wymianę danych między programami.

---

## Format plików CSV

### Eksport listy gatunków
```
# Autor;Jan Kowalski
# Data;2026-05-10
# Lokalizacja;52.412345, 16.923456 | Polana Bagno
# Powierzchnia;200 m²
# Ekspozycja;NW
# Nachylenie;15°
# Zwarcie A;70%
# ...

L.p.;Akronim;Nazwa łacińska;Nazwa polska;Ochrona;Warstwa;BB
1;Pinusylv;"Pinus sylvestris";"Sosna zwyczajna";"";A;3
```

### Eksport tabela BB (wiele zdjęć)
```
# Data;;; ;2026-05-10;2026-05-11
# Lokalizacja;;; ;Polana Bagno;Rezerwat X
...
Akronim;Warstwa;Nazwa łacińska;Nazwa polska;Zdjęcie 1;Zdjęcie 2
Pinusylv;A;"Pinus sylvestris";"Sosna zwyczajna";3;2
```

### Baza gatunków
```
skr;lac;pl;rodz;grra;grhg;prot;grp
```
- `skr` — akronim 8-znakowy
- `lac` — nazwa łacińska
- `pl` — nazwa polska
- `rodz` — rodzina
- `grra` — grupa Raunkiaera
- `grhg` — grupa fitosocjologiczna (Hennekens & Groenendijk)
- `prot` — status ochronny
- `grp` — grupa: `v` (naczyniowe), `b` (mszaki), `l` (porosty)

---

## Dane i prywatność

Aplikacja przechowuje wszystkie dane lokalnie w przeglądarce (`localStorage`):
- bieżące zdjęcie fitosocjologiczne
- archiwum zapisanych zdjęć
- ewentualnie zmodyfikowana baza gatunków

Żadne dane nie są wysyłane na serwer. Wyczyszczenie pamięci przeglądarki spowoduje utratę danych — zalecany regularny eksport CSV.

---

## Technologie

- Czysty HTML/CSS/JavaScript — bez frameworków, bez zależności zewnętrznych
- PWA (manifest + meta tagi) — instalacja na ekranie głównym
- `localStorage` — przechowywanie danych offline
- Web Speech API — rozpoznawanie głosowe (Chrome/Android)
- Geolocation API — pobieranie współrzędnych GPS

---

## Powiązane narzędzia

**FlorList** — siostrzana aplikacja do terenowej inwentaryzacji florystycznej (lista gatunków bez zdjęć fitosocjologicznych). Obie aplikacje korzystają ze wspólnej bazy gatunków w tym samym formacie CSV.

---

## Licencja

© 2026 Andrzej Rodziewicz — Arenaria sp. z o.o.

Udostępnione na licencji **CC BY-NC 4.0** (Creative Commons Uznanie autorstwa — Użycie niekomercyjne 4.0 Międzynarodowe).

Możesz swobodnie używać i modyfikować aplikację pod warunkiem podania autora i niekomercyjnego zastosowania. Komercyjne wykorzystanie wymaga pisemnej zgody autora.

# FastFrameFito — Arenaria

A mobile web application for conducting phytosociological relevés in the field. Works as a PWA (Progressive Web App) — installs on your phone's home screen and works like a native app, with no app store required.

> Designed for fieldwork: fast, intuitive, works offline.

---

## Installation on mobile

**Android (Chrome):**
1. Open the app URL in Chrome
2. Tap ⋮ → *Add to Home Screen*

**iPhone (Safari):**
1. Open the app URL in Safari
2. Tap the share icon □↑ → *Add to Home Screen*

---

## Features

### 🔍 Search
Panel for finding species and adding them to the current relevé.

- **Text search** — type at least 2 characters: 8-character acronym, Latin name, or Polish name. Results appear instantly.
- **Group filter** — buttons *All / Vascular / Bryophytes / Lichens* narrow the search pool.
- **Voice recognition 🎤** — microphone button allows dictating species names (Chrome on Android). Simply say e.g. *"Pinus sylvestris"*.
- **Layer popup** — after selecting a species, a popup appears for choosing the vegetation layer (A/B/C/D). One species can be added to multiple layers simultaneously.
- **Layer indicator** — species already added show which layers they occupy, e.g. `[AC]`.

### 📋 Relevé
Panel for the current phytosociological relevé with a full header.

#### Relevé header
- **GPS 📍** — automatic WGS84 coordinates (decimal degrees)
- **Relevé number / locality** — text field up to 60 characters
- **Author** and **Date**
- **Area** of the relevé (m²)
- **Aspect** (N, NE, E, SE, S, SW, W, NW, flat)
- **Slope** (°)
- **Cover of layers** A, B, C, D (%)
- **Height of layers** A and B (m)
- **Remarks** — text field up to 120 characters

#### Species table
Species sorted by layer A→B→C→D, then alphabetically within each layer. Columns: group (NAC/BRY/LIC), Latin name, Polish name, protection status, layer, BB value.

#### Braun-Blanquet abundance scale
| Value | Meaning |
|-------|---------|
| `5` | cover >75% |
| `4` | cover 50–75% |
| `3` | cover 25–50% |
| `2` | cover 5–25% |
| `1` | cover <5%, numerous |
| `+` | sparse, low cover |
| `r` | rare, solitary individuals |

#### Vegetation layers
| Layer | Description |
|-------|-------------|
| `A` | Tree layer |
| `B` | Shrub layer |
| `C` | Herb layer |
| `D` | Moss layer |

#### Action buttons
- **💾 Save** — saves the current relevé to the archive (or updates an existing one)
- **Clear** — removes all species from the current relevé
- **⬇ Export** — exports the current relevé (species list CSV or BB format)
- **✉ Mail** — sends the current relevé by email

### 📚 Archive
Panel for managing saved relevés.

- **Relevé list** — each relevé with locality/number, date, and species count
- **Checkboxes** — select any number of relevés; *Select all* button available
- **Open** — loads a relevé for editing in the Relevé panel
- **＋ New relevé** — clears the current relevé and starts a new one

#### Multi-relevé export
- **⬇ CSV list** — each selected relevé with full header as `#` comments, concatenated into one file
- **⬇ BB table** — classic phytosociological format: species × layers in rows, relevés in columns (compatible with JUICE and TurboVeg). Header metadata included as header rows.
- **✉ Send** — selected relevés in email body
- **🗑 Delete** — permanently removes selected relevés from the archive

### 🗄 Database
Panel for managing the built-in species database.

- **Database status** — species count by group: vascular, bryophytes, lichens
- **⬇ Export CSV** — downloads the full database as a CSV file
- **✉ Send database** — sends the database by email
- **⬆ Import CSV** — merges an imported CSV file with the existing database (new records added, existing ones updated)

---

## Acronym format

8-character acronyms: **first 4 letters of genus + first 4 letters of epithet**, e.g.:
- *Pinus sylvestris* → `Pinusylv`
- *Abies alba* → `Abiealba`
- *Vaccinium myrtillus* → `Vaccmyrt`

This format is compatible with the scheme used in JUICE and TurboVeg, facilitating data exchange between programs.

---

## CSV file formats

### Species list export
```
# Author;Jan Kowalski
# Date;2026-05-10
# Location;52.412345, 16.923456 | Polana Bagno
# Area;200 m²
# Aspect;NW
# Slope;15°
# Cover A;70%
# ...

No.;Acronym;Latin name;Polish name;Protection;Layer;BB
1;Pinusylv;"Pinus sylvestris";"Sosna zwyczajna";"";A;3
```

### BB table export (multiple relevés)
```
# Date;;; ;2026-05-10;2026-05-11
# Location;;; ;Polana Bagno;Reserve X
...
Acronym;Layer;Latin name;Polish name;Relevé 1;Relevé 2
Pinusylv;A;"Pinus sylvestris";"Sosna zwyczajna";3;2
```

### Species database
```
skr;lac;pl;rodz;grra;grhg;prot;grp
```
- `skr` — 8-character acronym
- `lac` — Latin name
- `pl` — Polish name
- `rodz` — family
- `grra` — Raunkiaer life form
- `grhg` — phytosociological group (Hennekens & Groenendijk)
- `prot` — protection status
- `grp` — group: `v` (vascular), `b` (bryophytes), `l` (lichens)

---

## Data and privacy

The application stores all data locally in the browser (`localStorage`):
- the current phytosociological relevé
- the archive of saved relevés
- any modified species database

No data is sent to any server. Clearing browser storage will result in data loss — regular CSV export is recommended.

---

## Technologies

- Pure HTML/CSS/JavaScript — no frameworks, no external dependencies
- PWA (manifest + meta tags) — home screen installation
- `localStorage` — offline data storage
- Web Speech API — voice recognition (Chrome/Android)
- Geolocation API — GPS coordinates

---

## Related tools

**FlorList** — a sister application for floristic field surveys (species list without phytosociological relevés). Both applications share the same species database format.

---

## License

© 2026 Andrzej Rodziewicz — Arenaria sp. z o.o.

Released under **CC BY-NC 4.0** (Creative Commons Attribution-NonCommercial 4.0 International).

You are free to use and modify the application provided you credit the author and do not use it commercially. Commercial use requires written permission from the author.
