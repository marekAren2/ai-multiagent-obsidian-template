# Wieloagentowy System Programistyczny (Obsidian & Conventional Commits Ready)

Podczas realizacji zadań programistycznych postępuj zgodnie z poniższym przepływem agentowym:

1. **@planner** - Tworzy plan architektoniczny i specyfikację. Przed rozpoczęciem sprawdzaj pliki `docs/Lessons_Learned.md` oraz `docs/Bugs_Log.md`, aby uniknąć znanych błędów z przeszłości.
2. **@coder** - Pisze wytypowany kod produkcyjny na podstawie planu.
3. **@git** - Tworzy commit: `feat: [opis zmian]`.
4. **@reviewer** & **@security** - Weryfikują jakość i bezpieczeństwo. Wszelkie wykryte błędy i podatności przekazują do naprawy oraz do udokumentowania.
5. **@git** - Wykonuje ew. commit z poprawkami: `sec: [opis poprawek]` lub `fix: [opis poprawek]`.
6. **@docs** & **@diagrams** - Generują dokumentację README.md oraz diagramy Mermaid, a także aktualizują rejestr błędów (`docs/Bugs_Log.md`) wraz z **diagramem Mermaid dla każdego problemu** wyjaśniającym jego mechanizm oraz wyciągają reguły na przyszłość (`docs/Lessons_Learned.md`) w formacie z natywnym wsparciem dla Obsidian (YAML Frontmatter, `#tagi`, `[[wikilinki]]`). Dokumentację specyficzną dla repozytorium kodu zapisują w centralnym repozytorium konfiguracji, w `docs/<slug-projektu>/` (np. `docs/test-project-code/`), a nie w repozytorium kodu. Globalne rejestry i dokumenty konfiguracji, takie jak `Bugs_Log.md`, `Lessons_Learned.md`, `Token_Metrics.md` i `Workspace_Setup.md`, pozostają bezpośrednio w `docs/`. Każdy dokument techniczny opisujący architekturę, przepływ danych lub moduł musi zawierać wyraźną sekcję z diagramem Mermaid (np. `flowchart` lub `sequenceDiagram`). Każdy nowo tworzony plik dokumentacji w `docs/` i jego podfolderach musi mieć nazwę `YYYYMMDD-HHMM_Nazwa_Pliku.md`, np. `20261021-1200_Logger.md`; przed utworzeniem sprawdź folder docelowy, kolizję nazwy i wymagany diagram. Przed zakończeniem zweryfikuj format nazwy oraz obecność diagramu. Przy aktualizacji istniejącego pliku canonical nie zmieniaj jego nazwy.
7. **@git** - Tworzy commit końcowy: `docs: zaktualizowano dokumentację, rejestr błędów i diagramy`.

Zasady ogólne:
- Pisz kod w pełni wytypowany i przetestowany.
- Używaj konwencji Conventional Commits.
- **Granica workspace:** Operuj wyłącznie w folderach wymienionych w aktywnym pliku `.code-workspace`. Rozwiązuj ścieżki względne względem tego pliku i uwzględniaj kanonikalizację ścieżek oraz symlinków. Nie odczytuj ani nie modyfikuj ścieżek poza workspace; jeśli zadanie wymaga takiej ścieżki, zatrzymaj się i poproś użytkownika o dodanie katalogu do workspace.
- **Ochrona `.env`:** Nigdy nie wysyłaj, nie załączaj, nie wklejaj ani nie przekazuj pliku `.env` lub jego zawartości do czatu, narzędzi zewnętrznych, repozytoriów ani usług. Nie wypisuj jego treści w logach, terminalu, diffach ani raportach. Nie dodawaj `.env` do stagingu, commitów ani uploadów; stage'uj jawne ścieżki zamiast używać poleceń zbiorczych, które mogłyby go objąć.
- Każdy diagram architektury oraz diagram troubleshootingowy (wyjaśniający błąd) musi być generowany w składni Mermaid.
- Każdy dokument techniczny opisujący architekturę, przepływ danych lub moduł musi zawierać wyraźną sekcję diagramu Mermaid, np. `flowchart` lub `sequenceDiagram`.
- Dokumentację repozytorium kodu zapisuj w centralnym repozytorium konfiguracji w `docs/<slug-projektu>/`; globalne rejestry pozostają w głównym `docs/`.
- Każdy nowo tworzony plik dokumentacji w `docs/` lub jego podfolderach musi mieć nazwę `YYYYMMDD-HHMM_Nazwa_Pliku.md`. Przed utworzeniem sprawdź format i kolizję nazwy; przed zakończeniem sprawdź nazwę i wymagany diagram. Nie zmieniaj nazw istniejących plików canonical, gdy są tylko aktualizowane.
- Każdy wykryty i naprawiony błąd musi zostać udokumentowany pod kątem unikania go w przyszłych projektach.
- **Oszczędzanie kontekstu i raportowanie tokenów:** Korzystaj tylko z kontekstu potrzebnego do zadania; czytaj pliki i powtarzaj informacje selektywnie, unikając zbędnych odczytów i powtórzeń. Odwołuj się do konkretnych plików, funkcji lub sekcji zamiast wklejać całe biblioteki. Raportuj tokeny tylko na podstawie wiarygodnego źródła telemetryki; nie wymyślaj ani nie przedstawiaj szacunków jako pomiarów. Gdy zapisujesz metryki, oznacz je jako `zmierzone`, `szacunek` albo `niedostępne`, podaj źródło lub metodę i założenia; niedostępnych wartości nie zgaduj. Rejestr prowadź w [[Token_Metrics]].
