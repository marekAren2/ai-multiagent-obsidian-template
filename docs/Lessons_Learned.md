---
aliases: [Zasady na Przyszłość]
tags: [projekt/szablon, typ/dobre-praktyki, obsidian]
created: 2026-10-21
---

# 📚 Zasady na Przyszłość (Lessons Learned)

Baza wiedzy z wyciągniętymi wnioskami i zasadami, do których agenci `@planner` i `@coder` odwołują się przed rozpoczęciem pracy.

---

## Ogólne Dobre Praktyki

### 1. Walidacja Wejścia i Parametryzacja
- **Zasada:** Nigdy nie łącz ciągów znaków w zapytaniach SQL/DB oraz zawsze waliduj parametry na poziomie middleware.
- **Tagi:** `#zasada` `#bezpieczeństwo` `#best-practice`

### 2. Typowalność i Clean Code
- **Zasada:** Każda funkcja i moduł muszą posiadać ścisłe typowanie. Unikaj stosowania typów niejawnych (np. `any`).
- **Tagi:** `#zasada` `#architektura` `#typowanie`

### 3. Bezpieczne indeksowanie tablic asocjacyjnych w Bash
- **Zasada:** Unikaj używania niezaufanych wartości jako indeksów tablic asocjacyjnych w skryptach Bash. Gdy zachowanie skryptu zależy od wersji Bash, sprawdź minimalną wymaganą wersję na początku działania.
- **Powiązane:** [[Bugs_Log]] · [[Workspace_Setup]]
- **Tagi:** `#zasada` `#bezpieczeństwo` `#bash` `#best-practice`

### 4. Filtry Git podczas checkoutu i merge
- **Zasada:** Traktuj checkout i merge Git jako operacje, które mogą uruchamiać lokalnie skonfigurowane filtry. Sprawdzaj i dokumentuj tę granicę zaufania przed aktualizacją plików.
- **Powiązane:** [[Bugs_Log]] · [[Workspace_Setup]]
- **Tagi:** `#zasada` `#bezpieczeństwo` `#git` `#best-practice`
