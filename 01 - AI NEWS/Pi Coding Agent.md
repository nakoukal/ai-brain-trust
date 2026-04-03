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



# I Hated Every Coding Agent, So I Built My Own — Mario Zechner (Pi)

> [!abstract] Shrnutí
> 
> Mario Zechner (tvůrce libGDX) vysvětluje svou frustraci ze stávajících kódovacích agentů (Claude Code, OpenCode), které považuje za příliš komplexní, nepředvídatelné nebo špatně navržené. Jako odpověď vytvořil **Pi** – minimalistického agenta se systémovým promptem pod 1000 tokenů a pouze čtyřmi základními nástroji, který lze plně ohýbat pomocí TypeScriptových rozšíření. [[02:12](http://www.youtube.com/watch?v=Dli5slNaJu0&t=132)]

## 🔗 Dokumentace a zdroje

- [Oficiální web Pi Agent](https://shittycodingagent.ai/)
    
- [GitHub repozitář (pi-mono)](https://github.com/badlogic/pi-mono)
    
- [Dokumentace k rozšířením a balíčkům](https://shittycodingagent.ai/packages)
    
- [Blog post Armina Ronachera o Pi](https://lucumr.pocoo.org/2026/1/31/pi/)
    

## ⚙️ Instalace a základní příkazy

Bash

```
npm install -g @mariozechner/pi-coding-agent
```

|**Příkaz**|**Popis**|
|---|---|
|`pi`|Spustí plně interaktivní terminálové rozhraní (TUI).|
|`pi -p "query"`|Provede jeden příkaz přímo z terminálu a vypíše výsledek.|
|`pi install npm:<name>`|Nainstaluje komunitní rozšíření nebo skilly.|
|`pi --version`|Ověření nainstalované verze agenta.|

## 💻 Praktické ukázky (Snippets)

[!example] Definice vlastního nástroje (Extension)

Pi je navržen tak, aby si uživatel mohl během minuty dopsat vlastní nástroje, které agent může používat.

TypeScript

```
import { Type } from '@mariozechner/pi-ai';

// Ukázka jednoduchého nástroje pro čtení souboru v Pi architektuře
const readTool = {
  name: 'read_file',
  description: 'Přečte obsah souboru',
  parameters: Type.Object({
    path: Type.String({ description: 'Absolutní cesta k souboru' })
  }),
  execute: async ({ path }) => {
    // Implementace čtení...
  }
};
```

## 📝 Klíčové poznámky

- **Filosofie minimalismu**: Pi obsahuje pouze 4 nativní nástroje: `read`, `write`, `edit` a `bash`. Vše ostatní (jako web search nebo sub-agenti) se řeší přes rozšíření. [[21:18](http://www.youtube.com/watch?v=Dli5slNaJu0&t=1278)]
    
- **Problém "Spaceship"**: Mario kritizuje Claude Code za to, že se z něj stává příliš komplikovaný nástroj, u kterého uživatel ztrácí přehled o tom, co AI dělá "za jeho zády" v kontextu. [[05:20](http://www.youtube.com/watch?v=Dli5slNaJu0&t=320)]
    
- **Kontrola nad kontextem**: Pi umožňuje detailní správu toho, co se posílá do LLM, včetně vlastních metod pro "compaction" (zkracování) historie chatu. [[11:45](http://www.youtube.com/watch?v=Dli5slNaJu0&t=705)]
    
- **YOLO Mode**: Pi defaultně nevyžaduje potvrzování každého kroku, protože Mario věří, že neustálé klikání na "Schválit" vede k únavě a ztrátě pozornosti. Bezpečnost řeší spíše izolací v kontejnerech. [[20:32](http://www.youtube.com/watch?v=Dli5slNaJu0&t=1232)]
    
- **Malleability (Tvarovatelnost)**: Agent by měl být schopen upravovat sám sebe. Uživatel může nechat Pi, aby mu napsal a nainstaloval nové rozšíření přímo během práce na projektu. [[23:06](http://www.youtube.com/watch?v=Dli5slNaJu0&t=1386)]
    

---