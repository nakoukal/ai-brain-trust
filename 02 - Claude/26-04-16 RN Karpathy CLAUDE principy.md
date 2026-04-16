---
title: Karpathy CLAUDE.md – 4 principy pro lepší AI agenty
date: 2026-04-16
tags:
  - zdroj/youtube
  - téma/claude-code
  - téma/prompt-engineering
  - téma/ai-agent-workflow
source: https://youtu.be/d8BGxfW3Vj4?si=RK7h6EBkNn9qjONH
github: https://github.com/forrestchang/andrej-karpathy-skills
---

# Karpathy CLAUDE.md – 4 principy pro lepší AI agenty

## Kontext

[Video: "The Karpathy CLAUDE.md File That 43,000 Developers Installed in 1 Week"](https://youtu.be/d8BGxfW3Vj4?si=RK7h6EBkNn9qjONH)

**Andrej Karpathy** (bývalý šéf AI v Tesle, spoluzakladatel OpenAI) popsal nejčastější chyby AI agentů při kódování. Vývojář **Forrest Chang** tyto poznatky přetavil do jednoho `CLAUDE.md` souboru — 43 000 vývojářů ho nainstalovalo za první týden.

> [!quote] Karpathy o problémech AI agentů
> *"They make wrong assumptions on your behalf and just run along with them without checking. They don't manage their confusion, don't seek clarifications, don't surface inconsistencies, don't present tradeoffs, don't push back when they should."*
>
> *"They really like to overcomplicate code and APIs, bloat abstractions, don't clean up dead code... implement a bloated construction over 1000 lines when 100 would do."*

> [!tip] Komplementární s [[Graphify – Knowledge Graph pro Claude Code]]
> Karpathy CLAUDE.md = **jak** Claude přemýšlí (chování agenta)
> Graphify = **co** Claude ví (kontext projektu)

---

## 4 hlavní principy

| Princip | Co řeší |
|---|---|
| **Think Before Coding** | Chybné předpoklady, skrytá nejasnost, chybějící tradeoffs |
| **Simplicity First** | Překomplikovaný kód, zbytečné abstrakce |
| **Surgical Changes** | Úpravy mimo rozsah zadání |
| **Goal-Driven Execution** | Imperativní příkazy místo deklarativních cílů |

---

### 1. Think Before Coding – Přemýšlej, než začneš kódovat

**Nepředpokládej. Neskrývej zmatek. Prezentuj tradeoffs.**

- Pokud není zadání jasné → **zeptej se místo hádání**
- Při více možných interpretacích → **prezentuj je explicitně**
- Pokud existuje jednodušší cesta → **řekni to**
- Pokud je něco nejasné → **pojmenuj to a zastav se**

> [!example] Ukázka
> Přepínač světlého režimu — Claude nejprve objasní záměr, teprve pak implementuje.

---

### 2. Simplicity First – Jednoduchost na prvním místě

**Minimum kódu, které řeší problém. Nic spekulativního.**

- Žádné funkce nad rámec zadání
- Žádné abstrakce pro jednorázový kód
- Žádná „flexibilita" nebo „konfigurovatelnost" bez vyžádání
- Žádné error handling pro nemožné scénáře
- Pokud lze 200 řádků napsat jako 50 → přepiš to

> [!tip] Test jednoducho sti
> Řekl by senior engineer, že je to překomplikované? Pokud ano, zjednodušit.

> [!example] Ukázka
> Vyhledávací panel: 20 řádků místo 50+ (standardní verze Claude).

---

### 3. Surgical Changes – Chirurgické změny

**Dotkni se jen toho, co musíš. Uklízej jen po sobě.**

Při úpravě existujícího kódu:
- **Nezlepšuj** přilehlý kód, komentáře ani formátování
- **Nerefaktoruj** věci, které nejsou rozbité
- **Odpovídej** existujícímu stylu, i když bys to dělal jinak
- Pokud vidíš nesouvisející mrtvý kód → **zmiň ho, nesmaž**

Pokud tvoje změny vytvoří sirotky:
- Odstraň importy/proměnné/funkce, které **tvoje** změny učinily zbytečnými
- Pre-existující mrtvý kód nemaž, pokud to není výslovně žádáno

> [!tip] Test chirurgičnosti
> Každý změněný řádek by měl přímo vycházet z uživatelova zadání.

---

### 4. Goal-Driven Execution – Provádění orientované na cíl

**Transformuj imperativní instrukce na deklarativní cíle s verifikační smyčkou.**

- Definuj **co** je výsledkem (kritérium úspěchu), ne jak to udělat
- Claude sám najde nejlepší cestu k cíli
- Pro vícekrokové úlohy: nejprve stručný plán, pak provedení

> [!example] Ukázka
> ❌ Imperativně: *"Přidej button, pak uprав styl, pak zaregistruj handler..."*
> ✅ Deklarativně: *"Uživatel musí být schopen vybrat ikonu agenta a vidět náhled."*

---

## Instalace

### Globálně (platí pro všechny projekty)

```bash
curl -o ~/.claude/CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md
```

### Nový projekt

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md
```

### Existující projekt (přidání k stávajícímu CLAUDE.md)

```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md >> CLAUDE.md
```

### Hierarchie CLAUDE.md souborů

| Umístění | Rozsah platnosti |
|---|---|
| `~/.claude/CLAUDE.md` | Globální – platí pro všechny projekty |
| `./CLAUDE.md` nebo `./.claude/CLAUDE.md` | Sdílený projektový layer (commituje se do gitu) |
| `./CLAUDE.local.md` | Osobní projektové poznámky (negituje se) |

> [!info] Doporučení
> Principy jsou navrženy tak, aby se **sloučily** s projektovými instrukcemi — přidej je k existujícímu `CLAUDE.md`, nepřepisuj ho.

---

## Srovnání s [[Graphify – Knowledge Graph pro Claude Code]]

| | Karpathy CLAUDE.md | [[Graphify – Knowledge Graph pro Claude Code\|Graphify]] |
|---|---|---|
| **Řeší** | Chování agenta | Kontext projektu |
| **Forma** | Textové instrukce | JSON knowledge graph |
| **Tvorba** | Manuální | Automatická |
| **Vhodné pro** | Všechny projekty | Velké codebases |

---

## Odkazy

- 🎬 **Video:** [The Karpathy CLAUDE.md File That 43,000 Developers Installed in 1 Week](https://youtu.be/d8BGxfW3Vj4?si=RK7h6EBkNn9qjONH)
- 📦 **GitHub repo:** [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)
- 📄 **Samotný CLAUDE.md:** [CLAUDE.md na GitHubu](https://github.com/forrestchang/andrej-karpathy-skills/blob/main/CLAUDE.md)
- 🐦 **Karpathy na X:** [@karpathy](https://x.com/karpathy) — [původní post](https://x.com/karpathy/status/2015883857489522876)
