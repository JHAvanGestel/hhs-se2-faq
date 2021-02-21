# Dit is de homepage.

### Klik op [Frequently Asked Questions](faq/intro.md) om naar de verschillende onderwerpen te gaan.

## Documentatie verbeteren:
De documentatie is geschreven in Markdown en gebouwd met DocFX
Door de onderstaande stappen te volgen kan de documentatie verbeterd of aangepast worden.  

### Vereisten
- Kennis van [Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
- Kennis van Git(hub)

### 1. Pull de laatste versie van de code naar je machine
Hiervoor kun je *gitbash* of elke andere tool gebruiken die git-functionaliteit biedt.

Je kunt niet direct de *master branch* bewerken.   
Om die reden zul je eerst een branch moeten aanmaken. 

### 2. Maak nieuwe documentatie aan en/of wijzig bestaande documentatie
Alle documentatie bevindt zich in de *docfx_project* folder.

Navigeer naar deze folder en vervolgens naar de folder FAQ.  
Deze folder bevat een aantal *.md bestanden en één toc.yml bestand.  

Het toc.yml bestand bevat een index van alle .md bestanden. 
Voeg hier een verwijzing toe als je een nieuw onderwerp wilt aanmaken.

Maak vervolgens een .md bestand aan en plaats daarin je content.

Het is ook mogelijk om de content van de bestaande .md bestanden te wijzigen.

### 3. Bouw de documentatie (website)
Zodra je klaar bent met het wijzigen van de content, is het zaak om de website te bouwen.

Navigeer in een terminal naar de rootfolder (hhs-se2-faq) en voer het volgende commando uit:

```bash
app\docfx.exe docfx_project\docfx.json
```

De website wordt nu gebouwd.   
Je zult één waarschuwing krijgen dat er geen project gedetecteerd is.
Dat is normaal.

Optioneel: Je kunt, met het volgende commando, een voorbeeld van de website bekijken voordat je hem publiceert.

```bash
app\docfx.exe serve docs
```
Er wordt nu op [deze site](http://localhost:8080) een pagina geserveerd.

### 4. Pull request maken
De laatste stap is het aanmaken van een pull request vanaf jouw branch naar de master-branch.  
Zodra deze is goedgekeurd en gemerged, zal de documentatie op de live website automatisch aangepast worden.  