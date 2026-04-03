
**Pi** je minimalistický, extrémně rozšiřitelný a "tvarovatelný" (malleable) kódovací agent. Na rozdíl od komplexních nástrojů sází na jednoduchost, transparentnost a plnou kontrolu uživatele nad kontextem.

## 📥 Odkazy ke stažení a instalaci

Pi je postaven na TypeScriptu a běží primárně v terminálu.

- **Oficiální web:** [pi.deaf](https://www.google.com/search?q=https://pi.deaf)
    
- **GitHub Repozitář:** [mastra-ai/pi](https://github.com/mastra-ai/mastra) (součást Mastra frameworku)
    
- **Instalace přes NPM:**
    
    Bash
    
    ```
    npm install -g @mastra/pi
    ```
    

---

## ⌨️ Základní příkazy

Aplikace se ovládá skrze terminálové rozhraní (TUI). Po spuštění příkazu `pi` v kořenovém adresáři projektu můžete používat:

|**Příkaz**|**Popis**|
|---|---|
|`pi`|Spustí agenta v aktuálním adresáři.|
|`pi --model <název>`|Spustí agenta s konkrétním modelem (např. `claude-3-5-sonnet`).|
|`/edit <soubor>`|Explicitní požadavek na úpravu konkrétního souboru.|
|`/compact`|Ruční spuštění komprese kontextu (vyčištění historie zpráv).|
|`/reset`|Vymaže aktuální session a začne s čistým štítem.|
|`Ctrl+C`|Ukončení session (uloží se do historie).|

---

## 💡 Filozofie nástroje

- **YOLO mode:** Žádné otravné potvrzování každého smazání souboru.
    
- **T-Max integrace:** Místo nepřehledných sub-agentů používá Pi klasické terminálové multiplexery.
    
- **Vlastní rozšíření:** Každý nástroj (bash, read, write) si můžete přepsat vlastním TypeScript skriptem přímo v projektu.
    

> [!tip] Tip pro Obsidian
> 
> Pokud používáte Pi k úpravě svých poznámek, nezapomeňte mu v systému nastavit cestu k vašemu Obsidian Vaultu, aby mohl indexovat vaše interní linky!

---

**Zdroj:** [Mario Zechner: I Hated Every Coding Agent...](https://www.youtube.com/watch?v=Dli5slNaJu0)