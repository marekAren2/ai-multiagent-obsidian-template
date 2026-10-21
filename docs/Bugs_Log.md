---
aliases: [Rejestr Błędów]
tags: [projekt/szablon, typ/rejestr-bledow, obsidian]
created: 2026-10-21
---

# 🐛 Rejestr Błędów i Problemów (Bugs Log)

Ten plik służy do śledzenia problemów wykrytych przez agentów `@security` i `@reviewer` oraz sposobu ich rozwiązania przez `@coder`. **Każdy wpis zawiera diagram Mermaid wyjaśniający mechanizm błędu.**

---

## Szablon Wpisu z Diagramem

### [YYYY-MM-DD] - Tytuł / Nazwa Błędu
- **Problem:** Krótki opis wykrytej podatności lub błędu w kodzie.
- **Przyczyna:** Dlaczego błąd powstał i jakie były warunki jego wystąpienia.
- **Wizualizacja błędu (Diagram Mermaid):**
  ```mermaid
  sequenceDiagram
      autonumber
      participant Klient
      participant API
      participant BazaDanych
      Note over Klient,BazaDanych: Przykład: Błędna walidacja wejścia (SQL Injection)
      Klient->>API: Zapytanie z nieoczyszczonym stringiem
      API->>BazaDanych: Surowe zapytanie SQL (Podatność!)
      BazaDanych-->>API: Zwrócenie danych
  ```
- **Rozwiązanie:** Opis zastosowanej poprawki (np. użycie sparametryzowanych zapytań).
- **Powiązane:** [[Lessons_Learned]]
- **Tagi:** `#bug` `#security` `#rozwiązany`

---

### [2026-10-21] - Zależność od wersji Bash i indeksy tablic asocjacyjnych
- **Problem:** Skrypt uruchamiał się na Bash 4+, używał `set -u` i indeksował tablice asocjacyjne niezaufanymi nazwami lub ścieżkami workspace. W starszym Bash indeks mógł doprowadzić do command-substitution injection, a puste tablice mogły powodować błąd unbound-variable.
- **Przyczyna:** Skrypt nie wymuszał wersji Bash, której zachowanie jest wymagane przez użyte indeksowanie tablic asocjacyjnych i `set -u`.
- **Efekt/Ryzyko:** W starszym Bash dane wejściowe mogły zostać wykonane jako podstawienie polecenia albo skrypt mógł nieoczekiwanie zakończyć działanie przy pustej tablicy.
- **Wizualizacja błędu (Diagram Mermaid):**
  ```mermaid
  flowchart TD
      A[Niezaufane nazwy lub ścieżki workspace] --> B[Indeks tablicy asocjacyjnej]
      B --> C[Starszy Bash]
      C --> D[Ryzyko command-substitution injection]
      C --> E[set -u i pusta tablica: unbound-variable]
      F[Wczesne sprawdzenie wersji Bash] --> G{Bash 5.2 lub nowszy?}
      G -->|Nie| H[Bezpieczne przerwanie]
      G -->|Tak| I[Kontynuacja na wspieranej wersji]
  ```
- **Rozwiązanie:** Ustalono wymóg Bash 5.2+ i dodano wczesne sprawdzenie wersji, które przerywa działanie na niewspieranej wersji.
- **Weryfikacja:** `bash -n` i test dry-run przeszły; pełnego wykonania skryptu nie testowano.
- **Status:** Naprawione.
- **Powiązane:** [[Lessons_Learned]] · [[Workspace_Setup]]
- **Tagi:** `#bug` `#security` `#rozwiązany` `#bash`

### [2026-10-21] - Lokalne filtry Git podczas aktualizacji workspace
- **Problem:** `git merge --ff-only` może checkoutować pliki i uruchamiać skonfigurowane lokalnie filtry Git `filter.*.smudge` lub `filter.*.process`; skrypt wcześniej nie sprawdzał tych filtrów.
- **Przyczyna:** Aktualizacja wykonywała fetch/merge bez kontroli lokalnej konfiguracji filtrów Git, które są wykonywane podczas checkoutu.
- **Efekt/Ryzyko:** Aktualizacja mogła uruchomić lokalnie skonfigurowany kod filtra na plikach pobieranych lub checkoutowanych w workspace.
- **Wizualizacja błędu (Diagram Mermaid):**
  ```mermaid
  flowchart TD
      A[Aktualizacja] --> B[Sprawdzenie lokalnej konfiguracji filtrów Git]
      B --> C{Aktywny filtr smudge lub process?}
      C -->|Tak| D[Przerwanie aktualizacji]
      C -->|Nie| E[Fetch i merge --ff-only]
      E --> F[Checkout plików]
  ```
- **Rozwiązanie:** Przed fetch/merge skrypt sprawdza lokalną konfigurację filtrów i przerywa aktualizację, jeśli wykryje aktywne filtry.
- **Weryfikacja:** `bash -n` i test dry-run przeszły; pełnego wykonania skryptu nie testowano.
- **Status:** Naprawione.
- **Powiązane:** [[Lessons_Learned]] · [[Workspace_Setup]]
- **Tagi:** `#bug` `#security` `#rozwiązany` `#git`
