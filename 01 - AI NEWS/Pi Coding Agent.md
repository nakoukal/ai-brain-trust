---
title: "I Hated Every Coding Agent, So I Built My Own — Mario Zechner (Pi)"
aliases:
  - Pi Agent
  - Pi Coding Agent
  - Mario Zechner Pi
tags:
  - youtube
  - technika
  - AI
  - programovani
source: "https://youtu.be/Dli5slNaJu0?si=Y4yR63AbJIZDQ6TL"
created: 2026-04-03
updated: 2026-04-03
author: "Gemini / Obsidian Architekt"
status: aktivní
description: Představení minimalistického kódovacího agenta Pi, který sází na extrémní rozšiřitelnost a kontrolu uživatele nad AI kontextem namísto složitých 'spaceship' funkcí.
---

## 📝 Stručný popis

Mario Zechner (tvůrce libGDX) představuje **pi**, radikálně minimalistický a rozšiřitelný terminálový AI agent pro programování. Projekt vznikl jako reakce na "přefouknutost" komerčních nástrojů a sází na transparentní práci s kontextem a vlastní TypeScript rozšíření.

## 🔗 Dokumentace a zdroje

- [Oficiální web Pi Agent](https://shittycodingagent.ai/)
    
- [GitHub repozitář (pi-mono)](https://github.com/badlogic/pi-mono)
    
- [Dokumentace k rozšířením a balíčkům](https://shittycodingagent.ai/packages)
    
- [Blog post Armina Ronachera o Pi](https://lucumr.pocoo.org/2026/1/31/pi/)
    
---

## 💻 Základní příkazy & Instalace

> [!info] Pi běží jako CLI nástroj v Node.js prostředí a vyžaduje API klíč (např. Anthropic).

|**Příkaz**|**Popis**|
|---|---|
|`npm install -g @pi-agent/cli`|Globální instalace agenta do systému.|
|`pi`|Spuštění v aktuálním adresáři projektu.|
|`pi --model opus`|Spuštění s konkrétním modelem (např. Claude 3.5 Opus).|
|`pi --reload`|Zapne hot-reload pro vývoj vlastních rozšíření.|

---

## 🛠 Praktické ukázky (Snippets)

### 1. Čtyři pilíře (Základní nástroje)

Pi dává modelu přístup pouze k těmto funkcím, což eliminuje zbytečnou komplexitu:

- `read_file` – Čtení souborů.
    
- `write_file` – Zápis celého souboru.
    
- `edit_file` – Cílené úpravy pomocí diffu.
    
- `bash` – Spuštění jakéhokoli příkazu v terminálu.
    

### 2. Tvorba vlastního toolu (TypeScript)

> [!example] Pi umožňuje psát si vlastní nástroje přímo v TypeScriptu a okamžitě je používat.

TypeScript

```
// .pi/tools/hello-world.ts
export const helloWorld = {
  name: "hello_world",
  description: "Jednoduchý testovací nástroj",
  execute: async ({ name }: { name: string }) => {
    return `Ahoj ${name}, vítej v Pi agentovi!`;
  }
};
```

---

## 🧠 Klíčové technické postřehy

> [!abstract] **Tree Sessions (Stromová historie)**
> 
> Historie v Pi není lineární chat, ale **strom**. Můžete se kdykoliv vrátit do historie, vytvořit novou větev (branch) a efektivně využívat **Prompt Caching**, což drasticky snižuje náklady na tokeny.

> [!tip] **Proč nepoužívat LSP během psaní?**
> 
> Mario varuje před posíláním chyb z LSP (Language Server Protocol) agentovi uprostřed práce. Kód je při psaní často nevalidní a tyto "chyby" model jen zbytečně matou. Validaci nechte až na moment, kdy agent prohlásí, že má hotovo.

> [!warning] **YOLO vs. Bezpečnost**
> 
> Pi nepoužívá otravné potvrzovací dialogy pro každý příkaz. Místo toho Mario doporučuje spouštět agenta v izolovaném kontejneru (Docker), kde může agent "přežít" i případné nebezpečné příkazy bez poškození hostitelského systému.

---

Stačí ti tato verze s opravenými uvozovkami, nebo chceš do poznámek přidat i sekci o tom, jak Mario bojuje proti "AI spamu" v Open Source?