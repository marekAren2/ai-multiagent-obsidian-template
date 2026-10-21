# Wieloagentowy System Programistyczny (Obsidian & Conventional Commits Ready)

Podczas realizacji zadań programistycznych postępuj zgodnie z poniższym przepływem agentowym:

1. **@planner** - Tworzy plan architektoniczny i specyfikację. Przed rozpoczęciem sprawdzaj pliki `docs/Lessons_Learned.md` oraz `docs/Bugs_Log.md`, aby uniknąć znanych błędów z przeszłości.
2. **@coder** - Pisze wytypowany kod produkcyjny na podstawie planu.
3. **@git** - Tworzy commit: `feat: [opis zmian]`.
4. **@reviewer** & **@security** - Weryfikują jakość i bezpieczeństwo. Wszelkie wykryte błędy i podatności przekazują do naprawy oraz do udokumentowania.
5. **@git** - Wykonuje ew. commit z poprawkami: `sec: [opis poprawek]` lub `fix: [opis poprawek]`.
6. **@docs** & **@diagrams** - Generują dokumentację README.md, diagramy Mermaid, a także aktualizują rejestr błędów (`docs/Bugs_Log.md`) wraz z **diagramem Mermaid dla każdego problemu** wyjaśniającym jego mechanizm oraz wyciągają reguły na przyszłość (`docs/Lessons_Learned.md`) w formacie z natywnym wsparciem dla Obsidian (YAML Frontmatter, `#tagi`, `[[wikilinki]]`).
7. **@git** - Tworzy commit końcowy: `docs: zaktualizowano dokumentację, rejestr błędów i diagramy`.

Zasady ogólne:
- Pisz kod w pełni wytypowany i przetestowany.
- Używaj konwencji Conventional Commits.
- Każdy diagram architektury oraz diagram troubleshootingowy (wyjaśniający błąd) musi być generowany w składni Mermaid.
- Każdy wykryty i naprawiony błąd musi zostać udokumentowany pod kątem unikania go w przyszłych projektach.
