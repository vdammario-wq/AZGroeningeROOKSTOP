# Rookvrij — AZ Groeninge Kortrijk

> **⚠️ Auteursrecht — lees dit eerst.**
> © Mario Van Dam. Alle rechten voorbehouden. Het ontwerp, de teksten en de
> opbouw van deze app zijn auteursrechtelijk beschermd. **Gebruik, verspreiding
> of nabouwen — geheel of gedeeltelijk — kan enkel met schriftelijke
> toestemming van de ontwerper.** Dit is geen open-sourceproject; de code staat
> hier ter beoordeling, niet ter overname. Zie [LICENSE.md](LICENSE.md).

Rookstopbegeleiding over 84 dagen, als installeerbare web-app (PWA).
Werkt volledig offline en zonder server: alle gegevens blijven op het
toestel van de gebruiker (localStorage). Geen account, geen login,
geen analytics.

## Inhoud

| Bestand | Wat |
|---|---|
| `index.html` | de volledige app: schermen, logica en de 84 dagteksten |
| `manifest.json` | app-naam, kleuren en iconen voor installatie |
| `sw.js` | service worker: offline gebruik |
| `logo.png` | logo AZ Groeninge (wordt in de schermen gebruikt) |
| `icon-192.png`, `icon-512.png` | app-icoon |
| `LICENSE.md` | auteursrechtverklaring — alle rechten voorbehouden |
| `HANDLEIDING.md` | korte handleiding voor gebruikers (installeren, demolinks) |
| `qr-rookvrij.png` | QR-code naar de gepubliceerde app |
| `fonts/` | lettertype Figtree en de licentie ervan |
| `.nojekyll` | zet Jekyll-verwerking op GitHub Pages uit |
| `.gitignore` | systeembestanden buiten de repo houden |

## Publiceren op GitHub Pages

De app is statisch: geen build, geen dependencies, geen server.

1. Maak op GitHub een nieuwe repository. Zet hem op **Private** als de app
   nog niet publiek mag; Pages werkt dan enkel op een betaald plan, dus voor
   een test met patiënten kies je **Public** en laat je de link ongedeeld.
2. Zet de inhoud van deze map in de **root** van de repository — dus
   `index.html` bovenaan, niet in een submap.
3. Settings → Pages → Source: **Deploy from a branch**, branch `main`,
   folder `/ (root)`. Bewaren.
4. Na een minuut staat de app op
   `https://GEBRUIKERSNAAM.github.io/REPONAAM/`. Dat is de URL voor je QR-code.
5. Open die URL op een gsm en zet de app op het beginscherm. De stappen voor
   Android en iPhone staan in [HANDLEIDING.md](HANDLEIDING.md).

HTTPS is nodig voor de service worker; GitHub Pages levert dat automatisch.

### Bij een update

De service worker cachet de app. Verhoog de versie bovenaan `sw.js`
(`rookvrij-v3` → `v4`) wanneer je `index.html` wijzigt, anders blijven
gebruikers de oude versie zien.

### Via de webinterface, zonder git

Repository → **Add file** → **Upload files** → alle bestanden uit deze map
selecteren → **Commit changes**. Bestanden die met een punt beginnen
(`.nojekyll`, `.gitignore`) worden door sommige bestandskiezers verborgen;
zet ze desnoods aan met **Create new file** en de naam handmatig.

## Demo zonder 84 dagen wachten

Voeg `?dag=NUMMER` toe aan de URL:

- `?dag=21` — mijlpaaldag tijdens de challenge
- `?dag=92` — vrije modus, tussen twee mijlpalen
- `?dag=100` — mijlpaal met tekst
- `?dag=365` — één jaar rookvrij

Vul eerst één keer de vragen in, zodat er een prijs per dag bekend is;
anders staat de teller op 0.

## Schermen

1. **Welkom** — wat de app doet, in drie regels.
2. **Wat rook je?** — sigaretten, tabak of vape (herbruikbaar of
   wegwerp), plus de buddy. Hieruit volgt de prijs per dag.
3. **Dagscherm** — dag x van 84 met de voortgangsring, het bespaarde
   bedrag, de quote van de dag en het stuk wetenschap. Op mijlpaaldagen
   (7, 14, 21 … 84) komt er een badge bij.
4. **Help!** — timer van vijf minuten, ademhalingsoefening (4-7-8),
   buddy bellen of WhatsApp, en het nummer van Tabakstop.
5. **Vrije modus** — na dag 84: dagen rookvrij, totaal bespaard, en op
   een mijlpaal de tekst die erbij hoort.
6. **Wat nog komt** — tijdlijn met de bedragen per mijlpaal, tot 20 jaar.
   De teksten zelf staan er niet: die lees je op de dag zelf.

## Huisstijl

| Rol | Hex |
|---|---|
| Achtergrond | `#FBF7F1` |
| Accent (gevuld) | `#F4A92D` |
| Tekst op accent | `#5c0f2d` |
| Tweede accent | `#7E153E` |
| Tekst | `#323232` |
| Hairline | `#EAE2D6` |

Font: Figtree, lokaal meegeleverd in `fonts/figtree.woff2` (SIL Open Font
License, zie `fonts/OFL.txt`). De app laadt dus niets van Google.

## Privacy

Er wordt niets verstuurd. De app slaat vier dingen lokaal op:
startdatum, prijs per dag, en naam en nummer van de buddy. Wissen van de
browsergegevens verwijdert ook de voortgang.

Een optionele koppeling met een rookstopcoach is ontworpen maar zit
**niet** in deze versie: dat vraagt een server en een GDPR-grondslag
(gezondheidsgegevens, art. 9).

## Auteursrecht

© Mario Van Dam. Alle rechten voorbehouden. Het ontwerp, de teksten en de
opbouw van deze app zijn auteursrechtelijk beschermd. Gebruik, verspreiding of
nabouwen kan enkel met schriftelijke toestemming van de ontwerper. Het logo en
de huisstijl van AZ Groeninge blijven eigendom van AZ Groeninge. Volledige
tekst: [LICENSE.md](LICENSE.md).
