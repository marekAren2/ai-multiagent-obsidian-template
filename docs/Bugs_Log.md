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
