# Zasady dotyczące zrzutów ekranu (Screenów)

Aby dokumentacja w repozytorium była spójna, czytelna i profesjonalna, przy dodawaniu zrzutów ekranu należy stosować się do poniższych zasad:

1. **Format plików:**
   * Wszystkie zrzuty ekranu zapisujemy w formacie **PNG** (zapewnia najlepszą ostrość tekstu i elementów interfejsu systemów Windows 11 / Windows Server 2025).

2. **Lokalizacja w repozytorium:**
   * Zrzuty ekranu dla danego ćwiczenia umieszczamy wyłącznie w dedykowanym katalogu `screeny/` wewnątrz folderu konkretnego tematu, np.:
     `cwiczenia/T04_instalacja_windows_server/screeny/`

3. **Nazewnictwo plików:**
   * Nazwy plików muszą być pisane **małymi literami**, bez polskich znaków i spacji (zamiast spacji stosujemy znak `_`).
   * Pliki numerujemy dwucyfrowo, aby zachować kolejność chronologiczną kroków w instrukcji:
     * `01_menu_instalatora_windows_server.png`
     * `02_wybor_wersji_desktop_experience.png`
     * `03_promowanie_do_kontrolera_domeny.png`

4. **Kadrowanie i czytelność:**
   * Robimy zrzuty **aktywnego okna** (skrót `Alt + PrintScreen` w Windows) lub wybranego fragmentu ekranu za pomocą *Narzędzia Wycinanie* (`Win + Shift + S`).
   * Unikamy zrzutów całego pulpitu w wysokiej rozdzielczości, jeśli kluczowy element jest mały i nieczytelny.
   * Zrzut powinien jednoznacznie pokazywać stan po wykonaniu danej operacji (np. zaznaczone opcje, wpisane komendy).

5. **Osadzanie w dokumentacji Markdown:**
   * W pliku `instrukcja.md` odwołujemy się do obrazu za pomocą wzoru:
     ```markdown
     ![Opis widoku, np. Wybór roli AD DS](./screeny/01_nazwa_pliku.png)
     ```
