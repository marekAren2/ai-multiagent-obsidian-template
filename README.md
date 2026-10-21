---
aliases: [Strona Główna Template]
tags: [projekt/szablon, typ/readme, obsidian]
created: 2026-10-21
---

# 🤖 AI Multi-Agent Starter Template for VS Code & Obsidian

Zestaw agentów AI (`@planner`, `@coder`, `@reviewer`, `@security`, `@docs`, `@diagrams`, `@git`) wspierający pełny cykl wytwarzania oprogramowania, automatyzację commitów Git oraz dokumentację zintegrowaną z **Obsidianem** (w tym automatyczne diagramy Mermaid dla każdego troubleshootingowego błędu).

## 📁 Struktura Projektu

- `.github/copilot-instructions.md` – Główny orkiestrator pętli agentowej.
- `.github/agents/` – Definicje 7 wyspecjalizowanych agentów AI.
- `docs/Bugs_Log.md` – Rejestr bazy problemów z diagramami Mermaid w formacie Obsidian (`#bug`, `[[wikilinki]]`).
- `docs/Lessons_Learned.md` – Baza zasad na przyszłość uwzględniana przez `@planner` przed tworzeniem specyfikacji.
- `.vscode/settings.json` – Ustawienia VS Code dla Copilota.

## 🚀 Jak Używać?

1. Skopiuj ten szkielet do swojego nowego projektu.
2. Otwórz folder w VS Code (oraz opcjonalnie jako Vault w Obsidianie).
3. W panelu **Copilot Chat** wywołuj agentów lub uruchamiaj pełną pętlę zgodnie ze wskazówkami z `copilot-instructions.md`.
