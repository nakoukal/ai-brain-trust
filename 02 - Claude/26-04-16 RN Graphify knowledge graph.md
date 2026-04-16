---
title: Graphify – Knowledge Graph pro Claude Code
date: 2026-04-16
tags:
  - zdroj/youtube
  - téma/claude-code
  - téma/knowledge-graph
  - téma/context-management
source: https://youtu.be/BkHps04qGgc
github: https://github.com/safishamsi/graphify
---

# Graphify – Knowledge Graph pro Claude Code

## Kontext

[Video: "Claude Code + Graphify = Instant Knowledge Graph (Free)"](https://youtu.be/BkHps04qGgc) od kanálu **FuturMinds**

**Graphify** řeší problém, kdy Claude Code re-čte stejné soubory při každé nové session. Místo toho projekt jednou zmapuje do knowledge grafu (JSON) a Claude čte tento graf — místo samotných souborů.

> [!tip] Komplementární s [[Karpathy CLAUDE.md]]
> Graphify = **co** Claude ví (kontext projektu)
> Karpathy CLAUDE.md = **jak** Claude přemýšlí (chování agenta)

---

## Jak Graphify funguje – 3 průchody

### Pass 1 – Parsing kódu
- Běží **lokálně**, bez volání API → **0 tokenů**
- Prochází strukturu projektu, třídy, funkce, závislosti

### Pass 2 – Dokumentace
- Zpracuje README, komentáře, docs

### Pass 3 – API shrnutí
- Jediný průchod přes Claude API → jednorázový token cost
- Vytvoří finální knowledge graph

> [!warning] Graph overhead
> Prvních **2–3 dotazů stojí více tokenů** než bez grafu.
> Úspora se projeví až po překročení crossover pointu.

---

## Instalace

```bash
# POZOR: dvě y na konci!
pip install graphifyy
```

> [!danger] Záměna balíčků
> `graphify` (jedno y) na PyPI je úplně jiný nástroj. Správně: `graphifyy` (dvě y).

---

## Reálná úspora tokenů

Benchmark **"71.5× fewer tokens"** je zavádějící:

- Porovnává proti scénáři, kdy vložíš **všechny soubory do kontextu najednou**
- Reálná Claude Code session neindexuje celý projekt — čte jen relevantní soubory
- Skutečná úspora závisí na velikosti projektu a počtu dotazů

> [!info] Kdy se Graphify vyplatí
> ✅ Velké codebases s mnoha soubory
> ✅ Časté dotazy na strukturu a závislosti
> ❌ Malé projekty (overhead převáží úsporu)
> ❌ Obsidian vault (poznámky nejsou kód)

---

## Aktualizace grafu

Po změnách v projektu je potřeba graf přegenerovat:

```bash
graphifyy update
```

---

## Srovnání s CLAUDE.md

| | [[Karpathy CLAUDE.md]] | Graphify |
|---|---|---|
| **Řeší** | Chování agenta | Kontext projektu |
| **Forma** | Textové instrukce | JSON knowledge graph |
| **Tvorba** | Manuální | Automatická |
| **Token cost** | Minimální | Jednorázový (Pass 3) + overhead |
| **Vhodné pro** | Všechny projekty | Velké codebases |

---

## Odkazy

- 🎬 **Video:** [Claude Code + Graphify = Instant Knowledge Graph](https://youtu.be/BkHps04qGgc)
- 📦 **GitHub:** [safishamsi/graphify](https://github.com/safishamsi/graphify)
