# Dokumentering

For at dokumentationen kan vedligeholdes og bruges i vores daglige arbejde, skal den have en veldefineret struktur og et klart formål. Denne side beskriver dokumentationens formål og struktur. Dette skal ses som en guide til hvordan man dokumenterer dashboards, kuber og databaser.


# Formål med dokumentation og GitHub

- Primære formål:
  - Give **overblik og indsigt** i vores dashboards, kuber og databaser. Dokumentationen skal kunne bruges i vores daglige arbejde og til besvarelser af postkassehenvendelser.
  - Gøre os opmærksomme på **fejl og uhensigtsmæssigheder** i opbygningen af vores dashboards, kuber og databaser.
  - Dokumentere **tankegangen** bag vigtige og komplekse beslutninger, så ræsonnement ikke bliver glemt eller går tabt.
  - Give os en **konsistent** måde at dokumentere og arbejde med dashboards, kuber og databaser.
  
- Sekundære formål:
  - Hjælpe **andre i Region Hovedstaden** med at forstå opbygningen af vores kuber og dashboards.

# Hvor, hvordan og hvornår dokumenterer vi?
Alle ændringer som laves i vores dashboards, *CHRU_HRKube* og views, samt i de tabeller som kuben bygger på skal dokumenteres. Dette gælder både når man tilføjer nye temaer og når man ændrer på allerede eksisterende. Vi dokumenterer vores arbejde følgende steder:
## Power BI-filer
Dashboards og de tilhørende infobokse skal **give et overblik** over hvad der vises på en given figur, samt hvilke measures den bygger på og hvilke filtre der er blevet brugt på figuren/siden. **Når man bygger dashboardet kommer alt dette naturligt med**.

## Kode-filer (DAX, SQL, Python osv.)
I koden indsætter man **korte kommentarer** som beskriver hvad bestemte linjer eller dele af koden gør. Beskriv som udgangspunkt **hvad koden gør** (f.eks. "Tæl antal ansatte") , ikke hvordan den gør det (dette beskriver koden ofte fint selv). Ved særligt komplekse udtryk kan en mere beskrivende tekst dog være nødvendig. De mere tekniske forklaringer skal så vidt muligt inkluderes som kommentarer i koden, og ikke på wiki-siden eller andre steder. Kommentarer i koden giver et bedre overblik og gør det lettere at genbruge dele af koden på et senere tidspunkt. **Man kommenterer normalt koden samtidigt med at man skriver den.**

## Tabular model (descriptions)
Alle measures, tabeller og kolonner skal have **en kort beskrivelse**. Denne "*description*" kan tilføjes i Tabluar Editor og bliver en del af den semantiske model. Dette betyder at man kan se beskrivelserne når man fx arbejder i Power BI. Beskrivelserne bliver også automatisk tilgængelige på vores wiki-side, hvor de er med til at give et overblik over kuben. Beskrivelsen skal som udgangspunkt **ikke være mere end 100 tegn, og den skal slutte med "*[værdi a, værdi b, ...]*"** som angiver et par eksempler på de værdier kolonnen eller measuret returnerer. **Man skriver normalt descriptions ind samtidigt med at man definerer measures, tabeller og kolonner i kuben**.

## Diskussionsforum og Issues
Her kan man skrive **spørgsmål eller ændringsforslag** ind. Dette sikrer dels at ændringsforslag ikke bliver glemt eller går tabt, samt at det ræsonnement som ligger til grund for beslutninger vedr. dashboards, kuben og databasen bliver gemt. Ofte giver det god mening at **konvertere et ændringsforslag til et Issue**, da dette bringer flere funktionaliteter med sig. Bl.a. er det muligt at kommentere på Issues og knytte "Pull requests" op på et Issue. På denne måde får man hele historikken med, og kan let se det ræsonnement som ligger til grund for ændringer i kuben, views og wiki-siden. OBS: vær opmærksom på at **Issues der oprettes i offentlige repositories som fx [*dokumentation*](https://github.com/DataOgDigitalisering/dokumentation) vil være offentligt tilgængelige**.

## Versionsstyring
Alle **ændringer i CHRU_HRKube** i udvikling og produktion skal ske gennem GitHub. Dette er med til at sikre at vi har et sikkert og stabilt miljø, hvor flere kan arbejde samtidigt. Alle **views som har skema-navnet "*chru_cube*"** og dermed ligger til grund for vores *CHRU_HRKube* skal også versionsstyres via. GitHub. Man kan læse mere om dette under [*versionsstyring*](./internt_versionsstyring). **Versionsstyringen skal ske sideløbende med at man skriver sin kode**.

## Wiki-siden
Wiki-siden samler al vores dokumentation og giver et overblik over vores miljøer og arbejdsgange. Alle ændringer i vores dashboards, kuber og datamodel kræver at man opdaterer wiki-siden så den ikke bliver uddateret. Her er en liste over hvad der skal dokumenteres på wiki-siden, samt hvornår i arbejdsprocessen man skal gøre det:
- Beskrivelse af alle **faner og figurer** i HR Strategisk Dashboard og HR Lederdashboard. Her er information om hvad figurerne viser samt hvilke definitioner og antagelser de bygger på. Alle measures som figuren bygger på og hele filterkonteksten er også beskrevet her. Dette kan bruges til at forstå hvordan figuren er bygget op og til besvarelse af postkassehenvendelser. **Denne dokumentation laves sideløbende med at man udvikler dashboardet, eller umiddelbart efter dashboardet er færdigudviklet**.
- Beskrivelse af **"*CHRU_HRKube*" i produktion**. Dette giver et overblik over alle measures, tabeller, relationer i kuben. **Denne dokumentation skrives sideløbende med at man arbejder i kuben, eller umiddelbart efter man har færdigudviklet det givne tema**.
- Beskrivelse af **views i produktion** med skema-navn "*chru_cube*". **Denne dokumentation skrives sideløbende med at man arbejder i kuben, eller umiddelbart efter man har færdigudviklet det givne tema**.
- Beskrivelse af tabeller og vores database. Dette giver en indsigt i hvordan tabeller er defineret og hvordan vores miljø er bygget op. **Denne dokumentation skrives sideløbende med at man tilføjer nye tabeller eller laver andre ændringer på vores database i produktion**.
- Beskrivelse af vores **arbejdsprocesser og de værktøjer** som vi bruger. Dette gælder dels brug at GitHub, wiki-siden, dokumentering og versionsstyring, men også hvordan man udvikler og arbejder med dashboards, kuber, views og tabeller. Dette er med til at sikre vi har en konsistent måde at arbejde på i alt fra navngivning af kolonner til opsætning af bogmærker i Power BI. **Denne dokumentation skrives løbende**.

# Skabeloner til dokumentation - UNDER UDVIKLING
De følgende afsnit beskriver hvordan dokumentationen af dashboards, measures og tabeller i kuben er bygget op. Man kan tage udgangspunkt i disse når man skal dokumentere et tema.

## Dashboards - dokumentation
Hver figur i dashboadet skal dokumenteres i hvert sit afsnit. Ansittet skal indeholde følgende:
- **Figurens navn**
- En **kort beskrivelse** af hvad figuren viser - dette kan suppleres med den tekst som står i info-boksene i selve dashboardet.
- En liste med alle de **measures, etiketter og farvekoder** som figuren benytter.
- En liste med alle de **filtre** som slår igennem på figuren, herunder:
  - Default-slicervalg som benyttes siden.
  - Filtreringer på siden.
  - Filtreringer på figuren.
  - Filtreringer i de measures som figuren benytter.
- Andre bemærkninger:
  - Vigtige tanker og overvejelser vedr. opbygning af figuren og afgrænsninger.
  - Eventuelle corner-cases man skal være opmærksom på.
  - Andet.

## Measures - dokumentation
Alle measures som er knyttet til et givent tema er beskrevet i kuben via. descriptions. Denne **metadata vises i et Excel-ark** med følgende oplysninger:
- Navnet på den folder som measuret hører under.
- Measurets navn.
- Returværdiens datatype og formatering.
- Det DAX-udtryk som definerer measuret.
- Beskrivelse af measuret og dets returværdier. Beskrivelsen skrives ind i Tabular Editor under feltet "description", og afsluttets med et par eksempler på measurets returværdier: "[a, b, ...]". Beskrivelsen skal angive hvad measuret beregner og evt. hvilke input-værdier measuret skal bruge. Yderligere kan man beskrive vigtige overvejelser, antagelser og definitioner som man skal være opmærksom på, når man benytter measuret.

Herudover kan **enkelte measures beskrives i deres eget afsnit**. Her kan man benytte følgende opbygning:
- Inputværdier/Filtreringer:
  - Angiv de filtrer og værdier measuret skal bruge. F.eks. en dato, personalegruppe osv.
- Returværdier:
  - Angiv hvad measuret returnerer.
- Uddybende bemærkninger:
  - Vigtige informationer om measuret. Hvad er dets funktion, hvordan bruges det, vigtige tanker og overvejelser omkring opbygning og afgrænsninger i measuret
  - Eventuelle corner-cases.
  - Oversigt over hvor measures indgår/relaterer til andre measures, hvis dette er relevant.

## Tabeller og kolonner - dokumentation
Alle tabeller og kolonner er beskrevet i selve kuben vha. descriptions. Denne **metadata vises i for hvert tema i et Excel-ark** med følgende oplysninger:
- **Navn på alle relevante tabeller**, hvornår de sidst er blevet **processeret** samt de **forespørgsler til SQL-severen** som de bygger på.
- **Beskrivelse af alle tabellerne** - fx "Indeholder svar, spørgsmål og respondent, bruges som fact-tabel". Beskrivelsen skrives ind i Tabular Editor under feltet "description".
- **Navn på alle kolonner** samt deres **datatype** og hvilken **kolonne de evt. sorteres efter**.
- **Beskrivelse af alle kolonner og deres værdier** - fx "Angiver det område spørgsmålet hører under [Løn, Tilhører ikke et område, ...]". Beskrivelsen skrives ind i Tabular Editor under feltet "description", og afsluttets med et par eksempler på kolonnens værdier: "[a, b, ...]".
- Oversigt over **alle relationer** som de relevante tabeller indgår i.

Herudover skal der for hver tabel være **et kort afsnit hvor tabellen er beskrevet i mere detalje**. Afsnittene indeholder følgende:

- Navn på tabellen
- Navn og link til de views som tabellen bygger på. Man skal linke til et view i denne mappe [https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder)

- Ekstra informationer om tabellen
  - vigtige tanker/overvejelser ved dannelsen af tabellen
  - vigtige tanker/overvejelser ved afgrænsning af data
  - Hvornår/hvordan opdateres den - skal den opdateres manuelt nogle gange (f.eks. hvis der er nogle værdier som er hard-coded ind el.lign.)
  - Andet
- Ekstra informationer om kolonnerne
  - Vigtige informationer om given tabel. Hvad er dens funktion, hvordan bruges den, vigtige tanker/overvejelser ved dannelsen af kolonner/afgrænsning af data. Hvornår opdateres den?
  - Dette skal suppleres af SQL og SAS-kode som skal være i sit eget repository på GitHub – gerne linket direkte til det her.
  - Andet
