



# Přehled kódu webové aplikace s více hrami

---

## 1. **Struktura HTML**

### a) **Hlavní části (sekce) her a menu**

- **Menu (úvodní obrazovka):**
  - Obsahuje tlačítka, která umožňují vybrat si různé hry.
  - Má ID `menu` a třídu `screen active` (viditelná při načtení).

- **Hry:**
  - Každá hra je v samostatném `<div>` s unikátním ID (`pexeso`, `ticTacToe`, `clicker`, `guessNumber`, `reactionTest`) a třídou `screen`.
  - Výchozí viditelná je pouze sekce menu; ostatní jsou skryté (`display: none`).

### b) **Speciální prvky her:**

- **Pexeso (paměťová hra):**
  - Hrací plán je `<div id="pexeso-board">`.
  - Po spuštění je naplněn kartami s obrázky (emoji).

- **Piškvorky (tic-tac-toe):**
  - Hrací plán je `<div id="ttt-board">`.
  - Vedle je `<p id="ttt-status">` pro zobrazení výsledku.

- **Clicker:**
  - Ukazuje počet bodů a tlačítko pro klikání.

- **Hádej číslo:**
  - Input pro zadání čísla a tlačítko pro hádání.

- **Reakční test:**
  - Zobrazí zprávu a tlačítko pro start/testování reakčního času.

---

## 2. **Stylování (CSS)**

- **Celé tělo:**
  - Používá sans-serif font, centrované texty, světlé pozadí.
- **Sekce her (`.screen`):**
  - Výchozí je `display: none`, třída `.active` je nastaví na `display: block`.
- **Tlačítka:**
  - Mírné okraje, polštáře, velké písmo, kurzor pointer.
- **Pexeso:**
  - Mřížka 6 sloupců, jednotlivé karty mají fixní velikost, stín a zaoblení rohů.
  - Karty s třídou `matched` mění barvu a kurzor na default.

---

## 3. **JavaScript – Funkcionalita**

### a) **Navigace mezi obrazovkami**

- **`goBack()`**: Přepne zpět na hlavní menu.
- **`showGame(gameId)`**: Přepne na vybranou hru podle ID a spustí její inicializaci.

---

### b) **Hra Pexeso**

- **Popis:**
  - 18 párů emoji, celkem 36 karet.
  - Karty jsou náhodně zamíchány.
- **Fungování:**
  - Kliknutím na kartu se zobrazí emoji.
  - Pokud je to první karta, uloží se do `pexesoFirst`.
  - Pokud je druhá, porovná se s první:
    - Pokud se shodují, obě jsou označeny jako `matched`.
    - Pokud ne, po 1 sekundě se zakryjí zpět.
  - Vyhraje, když jsou všechny páry najdené.

### c) **Piškvorky (tic-tac-toe)**

- **Popis:**
  - 3x3 mřížka, hráči střídají X a O.
  - Výsledek je oznámen po výhře nebo remíze.
- **Fungování:**
  - Kliknutím na buňku se zapíše symbol X/O.
  - Kontroluje se, jestli někdo vyhrál nebo je remíza.
  - Restart hry resetuje stav.

### d) **Clicker (klikací hra)**

- **Popis:**
  - Po každém kliknutí se zvýší skóre.
- **Fungování:**
  - Funkce `clickerClick()` zvyšuje počet bodů a aktualizuje zobrazení.

### e) **Hádej číslo**

- **Popis:**
  - Generuje náhodné číslo od 1 do 100.
  - Uživatel hádá číslo, dostává zpětnou vazbu.
- **Fungování:**
  - Funkce `checkGuess()` porovnává hádané číslo s tajným.
  - Pokud je správně, zobrazí gratulaci, jinak naznačí jestli je příliš malé nebo velké.
  - Vložení nového čísla resetuje hru.

### f) **Reakční test**

- **Popis:**
  - Čeká na náhodný čas, po kterém se aktivuje tlačítko „Klikni“.
  - Čas reakce se měří od začátku do kliknutí.
- **Fungování:**
  - Funkce `startReactionTest()` nastaví náhodný čas, pak zobrazí výzvu.
  - `measureReaction()` spočítá čas a vypíše ho.

---

## 4. **Obecné ovládání a inicializace**

- **`showGame()`**: Přepíná mezi hrami a volá jejich inicializační funkce.
- **`goBack()`**: Vrací na hlavní menu.
- **Hry mají vlastní funkce pro spuštění a resetování:**
  - Pexeso: `startPexeso()`
  - Piškvorky: `startTicTacToe()`
  - Clicker: `initClicker()`
  - Hádej číslo: `resetGuess()`
  - Reakční test: `resetReactionTest()`

---

## 5. **Celkový tok programu**

- Po načtení stránky se zobrazí hlavní menu.
- Kliknutím na tlačítko se přepne na vybranou hru.
- Po hraní nebo kliknutí na „Zpět do menu“ se vrátíš zpět na hlavní menu.
- Každá hra má své vlastní logiky a interaktivní prvky.

---

Pokud bys chtěl, můžu ti také pomoci s vylepšením nebo rozšířením jednotlivých her. Stačí říct!
