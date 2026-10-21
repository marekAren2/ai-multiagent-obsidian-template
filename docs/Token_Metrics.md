---
aliases: [Statystyki Tokenów i Kosztów]
tags: [projekt/szablon, typ/metryki, obsidian]
created: 2026-10-21
---

# 📊 Rejestr Zużycia Tokenów

Rejestr służy do śledzenia zużycia kontekstu i optymalizacji pracy agentów. Sam Copilot Chat może nie udostępniać telemetryki tokenów, dlatego wpisy muszą jasno wskazywać status i źródło danych.

## Zasady raportowania

- `zmierzone` oznacza wartość odczytaną z wiarygodnego źródła telemetryki.
- `szacunek` oznacza wartość wyliczoną metodą opisaną we wpisie; nie należy przedstawiać jej jako pomiaru.
- `niedostępne` oznacza brak wiarygodnych danych. W takim wpisie wartości tokenów i kosztu pozostają `N/D`.
- Koszt podawaj tylko wtedy, gdy znane są stawki dla użytego modelu i źródło pomiaru. Nie wyprowadzaj kosztu z niepotwierdzonych założeń.
- Zużycie zależy od modelu, długości kontekstu i rodzaju zadania; nie zakładaj uniwersalnego rankingu agentów bez porównywalnych pomiarów.
- Zapisuj metryki, gdy wiarygodna telemetria jest dostępna lub gdy użytkownik prosi o raport. Nie dopisuj automatycznie pustego wpisu do każdego zadania.

## Log sesji i zadań

| Data | Zadanie / sesja | Model / agenci | Status | Tokeny wejściowe | Tokeny wyjściowe | Koszt | Źródło / metoda | Optymalizacja / uwagi |
| :--- | :--- | :--- | :--- | ---: | ---: | ---: | :--- | :--- |
| YYYY-MM-DD | Opis zadania | Model, `@agent` | `zmierzone` / `szacunek` / `niedostępne` | N/D | N/D | N/D | Źródło telemetryki, metoda lub `brak` | Zmiana ograniczająca zbędny kontekst |

## Praktyki ograniczania kontekstu

- Zlecaj agentom konkretny zakres plików i zachęcaj do odczytu tylko fragmentów potrzebnych do zadania.
- Odwołuj się do konkretnych plików, symboli lub sekcji zamiast wklejać całe biblioteki i długie źródła.
- Unikaj powtarzania w promptach informacji już dostępnych agentowi.
- Gdy `[[Lessons_Learned]]` lub `[[Bugs_Log]]` urosną, rozważ krótkie indeksy tematyczne i archiwizację historycznych wpisów zamiast wczytywania całej historii.
- W Copilot Chat można dołączyć konkretny plik przez `#file:`; dołączaj tylko materiały istotne dla bieżącego zadania.

Powiązane: [[Lessons_Learned]] · [[Bugs_Log]] · [[README]]