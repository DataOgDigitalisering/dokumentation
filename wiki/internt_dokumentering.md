# Dokumentering - under udvikling

For at dokumentationen kan vedligeholdes og bruges i vores daglige arbejde, skal den have veldefineret struktur og et klart formål. Denne side beskriver dokumentationens formål og struktur. Dette skal ses som en guide til hvordan man dokumenterer dashboards, kuber og databaser.


# Formål med dokumentation og GitHub

- Primære formål:
  - Give **overblik og indsigt** i vores dashboards, kuber og databaser. Dokumentationen skal kunne bruges i vores daglige arbejde og til besvarelser af postkassehenvendelser.
  - Gøre os opmærksomme på **fejl og uhensigtsmæssigheder** i opbygningen af vores dashboards, kuber og databaser.
  - Dokumentere **tankegangen** bag vigtige og komplekse beslutninger, så ræsonnement ikke bliver glemt eller går tabt.
  - Give os en **konsistent** måde at dokumentere og arbejde med dashboards, kuber og databaser.
  
- Sekundære formål:
  - Hjælpe andre i Region Hovedstaden med at **forstå opbygningen** af vores kuber og dashboards.

# Hvor, hvordan og hvornår dokumenterer vi?
Vi dokumenterer vores arbejde følgende steder

## Power BI-filer
Dashboards og de tilhørende infobokse skal **give et overblik** over hvad der vises på en given figur, samt hvilke measures den bygger på og hvilke filtre der er blevet brugt på figuren/siden. **Når man bygger dashboardet op kommer alt dette naturligt med**.

## Kode-filer (DAX, SQL, Python osv.)
I koden indsætter man **korte kommentarer** som beskriver hvad bestemte linjer eller dele af koden gør. Beskriv som udgangspunkt **hvad koden gør** (f.eks. "Tæl antal ansatte") , ikke hvordan den gør det (dette beskriver koden ofte fint selv). Ved særligt komplekse udtryk kan en mere beskrivende tekst dog være nødvendig. De mere tekniske forklaringer skal så vidt muligt inkluderes i kommentarer i koden, og ikke på hjemmesiden eller andre steder. Kommentarer i koden giver et bedre overblik og gør det lettere at genbruge dele af koden på et senere tidspunkt. **Man kommenterer normalt koden samitidigt med at man skriver den.**

## Tablar model (descriptions)
Alle measures, tabeller og kolonner skal have **en kort beskrivelse**. Denne "description" kan tilføjes i Tabluar Editor og bliver en del af den semantiske model. Dette betyder at man kan se beskrivelserne når man f.eks. arbejder i PowerBI. Beskrivelserne bliver også automatisk tilgængelige på vores wiki-side hvor de er med til at give et overblik over kuben. Beskrivelsen skal som udgangspunkt **ikke være mere end 100 tegn, og den skal slutte med "*[værdi a, værdi b, ...]*"** som angiver et par eksempler på de værdier kolonnen eller measuret returnerer. **Man skriver normalt descriptions ind samtidigt med at man definerer measures, tabeller og kolonner i kuben**.

## Diskussionsforum og Issues
Her kan man skrive **spørgsmål eller ændringsforslag** ind. Dette sikrer dels at ændringsforslag ikke bliver glemt eller går tabt, samt at det ræsonnement som ligger til grund for beslutninger vedr. dashboards, kuben og databasen bliver gemt. Ofte giver det god mening at **konvertere et ændringsforslag til et Issue**, da dette bringer flere funktionalister med sig. Bl.a. er det muligt at kommentere på Issues og knytte "Pull requests" op på et Issue. På denne måde får man hele historikken med, og kan let se det ræsonnement som ligger til grund for ændringer i kuben, views og wiki-siden. OBS: vær opmærksom på at **Issues der oprettes i offentlige repositories som f.eks. "dokumentation" vil være offentligt tilgængelige**.

## Versionsstyring
Alle ændringer i CHRU_HRKube i udvikling og produktion skal ske gennem GitHub. Dette er med til at sikre vi har et sikkert og stabilt miljø hvor flere kan arbejde samtidigt. Alle views som har skema-navnet "*chru_cube*" og dermed ligger til grund for CHRU_HRKube'en skal også versionsstyres via. GitHub. Man kan læse mere om dette under TODO VERSIONSSTYRING. **Versionsstyringen kan ske sideløbende med at man skriver sin kode, eller når man er klar til at impleneterer sine ændringer i vores fælles kuber**.

## Wiki-siden
Wiki-siden samler alt vores dokumentaiton og giver et overblik over vores miljøer og arbejdsgange. Alle ændrigner i vores dashboards, kuber og datamodel kræver at man opdaterer wiki-siden så den ikke bliver uddateret. Wiki-siden består af flere dele
- Besrkivesle af alle faner og figurer i HR Strategisk Dashboard og HR Lederdashboard. Her er information om hvad figurerne viser samt hvilke definitioner og antagelser de bygger på.



- Hjemmeside (Dashboards, kuber, views) - overblik Øvesler - afsnit med hvordan man bygger/bruger vores værktøjer/miljø

  
# Hvor dokumenterer vi vores arbejde og værktøjer vi bruger til det

- Dokumentationen på GitHub skal give overblik over tabeller og measures og deres relationer. 
- Den skal angive hvordan de bruges, hvad de returnerer/viser og beskrive vigtige overvejelser/antagelser/definitioner man skal være opmærksom på når man bruger kuben og trækker tal.

Værktøjer og overvejelser:
- Vigtigt med afsnit om hvordan man bygger nye temaer op, så vi navngiver konsistent osv.
- Vigtigt at have et sted hvor man beskriver hvordan man filtrerer på stilling og DimOrganisation (til folk som skal bygge nye dashboards f.eks.)
- Vigtigt at dokumentationen giver en klar forståelse af de grundlæggende definitioner vi arbejder med som f.eks. fratrædelse, ansatte, tiltrædelse osv.
- Overvej hvor/hvad vi kan trække ift. versionsstyring/vedligeholdelse:
- SSMS: 
  - Database: view-definitioner, oversigt over tabeller og views, hvor de bruges osv.
  - Kuben: billede af model og relationer – Nicolai viste dette
- Tabular Editor
  - Alle tabeller, kolonner, beskrivelser
  - Hvordan tabeller og measures bygger på hinanden – Nicolai viste Excel-dok
- Power BI
  - Hvor measures bruges, hvilke der ikke bruges osv. – Nicolai nævnte kort at dette (måske…) var en mulighed
- Overvej at bruge GitHub som platform/dialogområde ift. valg truffet i kuben og diskussioner, så vi ikke overser/glemmer noget og har gemt tankerne/dialogen et sted.

# Strukturen på dokumentation
- Tabeller
  - Beskrivelse af selve tabellen (ikke mere end 100 tegn).
  - Liste over alle kolonner (minder om SD’s dokumentation):
  - Key, Kolonnenavn, Datatype, Len, Null’s, Beskrivelse af hvad kolonnen viser (ikke mere end 100 tegn) med eksempel på værdi
  - Beskrivelse skal ind som ”description” i TabularEditor – dvs. listen kan stort set autogenereres…
  - Beskrivelse/Resume af hver tabel:
  - Vigtige informationer om given tabel. Hvad er dens funktion, hvordan bruges den, vigtige tanker/overvejelser ved dannelsen af kolonner/afgrænsning af data. Hvornår opdateres den?
  - Billede af datamodel og liste over relationer.
  - Dette skal suppleres af SQL og SAS-kode som skal være i sit eget repository på GitHub – gerne linket direkte til det her.

- Measures
  - Liste over alle measures indenfor temaet – ligesom for tabellerne
  - Measurenavn, returnType, Beskrivelse af measure (ikke mere end 100 tegn) med eksempel på returnValue.
  - Beskrivelse skal ind som ”description” i TabularEditor – dvs. listen kan stort set autogenereres.
  - Beskrivelse/Resume af hvert measure:
  - Vigtige informationer om measure’et. Hvad er dens funktion, hvordan bruges den, vigtige tanker/overvejelser ved opbygning/afgrænsninger i measure, eventuelle faldgrupper/corner-cases osv.
  - Oversigt over hvor measures indgår/relaterer til hinanden.
  - Dette skal suppleres af et repository i GitHub med hele kuben og alle measures som man kan linke til. Det skal måske også suppelers med ExcelFil over hvordan measures bygger på hinanden/hvor de bruges i dashboards/hvilke der ikke bruges i dashboards.

- Dashboards
  - Forbehold
    - Dels tror jeg ikke at jeg vil komme til at bruge det i dagligdagen, kun når jeg skal sætte mig ind i et tema fra bunden. Ellers tager det for lang tid at finde de svar man søger.
    - Vedligeholdelse bliver et stort arbejde hvis det kommer med. 
- Skal dokumentere filtre og figurer (klar struktur, overvej vedligeholdelse + hvor der skal dokumenteres)
- FAQ ved siden af?


