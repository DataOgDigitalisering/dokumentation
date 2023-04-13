# Dokumentering

For at dokumentaitonen kan vedligeholdes og bruges i vores daglige arbejde kræver det at den har veldefineret struktur og et klart formål. De følgende afsnit beskriver dokumentationens formål og struktur. Dette skal ses som en guide til hvordan man dokumenterer sit arbejde.


# Formål med dokumentation
- Primære formål:
  - Virke som opslagsværk der giver overblik og indsigt i vores dashboards, kuber og databaser. Dokumentationen skal kunne bruges i vores daglige arbejde og til bevsvarelser af postkassehenvendelser.
  - Gøre os opmærksomme på fejl og uhensigtsmæssigheder i opbygningen af vores dashboards, kuber og databaser.
  - Dokumentere tankegangen bag vigtige og komplekse beslutninger, så ræsonnement ikke bliver glemt eller går tabt.
  - Give os en konsistent måde at dokumentere og arbejde med dashboards, kuber og databaser.
  
- Sekundære formål:
  - Hjælpe andre i Region Hovedstaden med at forstå opbygningen af vores kuber og dashboards.
  
# Hvor dokumenterer vi vores arbejde og værktøjer vi bruger til det

Vi dokumenterer flere steder:
- Dashboards og infobokse giver overblik over hvad der vises/hvilke measures/filtre som virker på de enkelte figurer. Bliver et stort arbejde at dokumentere og vedligeholde dette i GitHub, men skal dokumenteres på en eller anden måde.
- Koden/kommentarer i measures beskriver hvordan koden er bygget op, hvilke funktioner man bruger, hvilke filtre man bruger. Det bliver hurtigt uoverskueligt at tage dette med ind i dokumentationen i GitHub, både ift. at læse det og vedligeholde det.
- Dokumentationen på GitHub skal give overblik over tabeller og measures og deres relationer. Den skal angive hvordan de bruges, hvad de returnerer/viser og beskrive vigtige overvejelser/antagelser/definitioner man skal være opmærksom på når man bruger kuben og trækker tal.
- Øvelser som kan hjælpe med og sikre at man forstår hvordan measures og tabeller bruges inden for givent tema/emne.

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


