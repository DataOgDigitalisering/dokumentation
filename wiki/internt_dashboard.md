# Introduktion
Denne side beskriver de ting som man skal være opmærksom på når man bygger og arbejder med dashboards. Siden omhandler alt fra navngivning af bogmærker til best practice når man tiløjer filtre. Også mere avancerede ting som automatisk drill down på visualiseringer er beskrevet.

# Brugerstyring og sikkerhed
Hvis man vil dele sit dashboard med andre og lægge det op på FLIS skal man være opmærksom på hvem der kan tilgå dashboardet. Man kan se hvem der har adgang til filen ved at klikke på *...* til højre for filen, vælge *Manage* og herefter klikke på *Security*. Nogle personer bliver automatisk tilføjet som læsere når man uploader en Power BI fil til serveren. Det er derfor vigtigt at man altid tjekker hvem der har adgang efter man har uploadet sin fil. Under *Manage* kan man også sætte en systembruger op, hvis det er nødvendigt.

# Navngivning af faner
Fanerne i dashboardet nanvgives på følgende måde:
- Den centrale side for et givent tema kalder man bare temaets navn. F.eks. "*Trivsel*"
- Undersider til det givne tema nanvgiver man "*SUB*", f.eks. "*SUB - Organisationsherakisk*".
- Siden med filtervalg nanvgiver man "*FV*", f.eks. "*FV - Trivsel*"
- Siden med tooltips nanvgiver man "*TT*", f.eks. "*TT - Tirvsel - Hovedstillingsgruppe*".

Rækkefølgen på fanerne er også vigtig. Her er kommer alle temaer og deres tilhørende undersider først. Herefter kommer alle sider med filtervalg, og til sidst kommer alle sider med tooltips. Dette kan f.eks. ses i HR Strategisk Dashboard.
# Selection - gruppering af objekter
Alle objekter som figurer, knapper og tekstfelter skal grupperes. Dette gør det f.eks. lettere at holde styr på layer order og bogmærker. Under fanen "View" i Power BI kan man vælge at få fanen "*Selection*" vist. Det vigtigste er at man har de fire grupperinger:
 - "*Info*" - hvor alle objekter og tekstbokse som bliver vist i infoboksen er med.
 - "*Generelt*" - hvor overskift, logo og tekst som beskriver opdateringskadancen er med.
 - "*Filtre*" - som indeholder alle slicers, bokse mm. som danner filtrene i højre side af dashboardet.

TODO SELECTIONS

Herudover er det ofte en god idé at gruppere figurer og visualiseringer. Man skal være opmærksom på at rækkefølgen på objekterne i "Selection" styrer deres layer order. **Det er også en god idé at slå  "*Maintain Layer order*" til på alle figurer og knapper**, så de ikke "bytter" plads når man klikker på dem i det færdige dashboard.

TODO LAYER ORDER

# Format på figurer og tekster
Dashboardsne benytter bestemte farver, skrifttyper, skriftstørelser osv. Nogle af disse farvekoder er gemt i kuben under "*_Farver*" og kan refereres til gennem Power BI. Andre er tastet manuelt ind på den givne figur. **Det er ofte en god idé at kopiere en figur som allerede er i dashboardet** og tage udgangspunkt i denne. På den måde sikrer man sig at skrifttype, skriftstørelse mm. er identiske. Overskrifter skriver man normalt ind manuelt med mindre den optræder flere steder eller skal være dynamisk. Hvis overskfiten skal være dynamisk kan man gemme den i kuben under "*_Tekster*".

# Filtre - på siden, på figuren, i measuret


# Filter på stilling og organisation


# Sync slicers


# Bogmærker
# Nulstil, Infoboks, vis filtervalg



# Automatisk drilldown på visualiseringer
## Funktionen anvendes på hierarkisk struktureret data og gør det muligt at automatisk få vist det nedre niveau, når man har filtreret på det øvre niveau. 
Se Exitdashboard for et udvidet eksempel.

Power BI understøtter desværre ikke denne funktion som standard, men ved brug af en hjælpetabel, to measures og et filter på visualisering, kan funktionen opnås.

## Hjælpetabellen

Det er nødvendigt at have en hjælpetabel, som indeholder det fulde heiraki. 
Eksempel på hjælpetabellens struktur fra kursusportal dashboard. 

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Kursus | Kursusnavn |
| 2 | Kursus |  Kursusnavn |
| 1 | Hold | Holdnavn |
| 2 | Hold |  Holdnavn |

Se Kube tabellen **v_DimOrgDrill** for et mere fyldestgørende eksempel

Tabellen er opbygget som Union af hvert enkelt udsnit af hierarkiet, Hvor ID gentages for hvert niveau. 

Tabellen tilføjes til resten af datamodellen via enten en begge vejet mange til mange relation eller en begge vejet bridge tabel.  
## Measure til at bestemme aktivt niveau i hierarkiet 
```
Drill filter = IF(HASONEFILTER([Den Tabelkolonne som er slicer]),"Navn på næste nedre niveau","Navn på topniveau")
```

Her ses hvordan det fungere for kursusportalen. Et kursus kan have flere hold og vi ønsker at visualiseringen skifter til hold niveau, når man har anvendt sliceren til at filtrere et bestemt kursus frem. Vis man vælger flere kurser, vises visualiseringen på kursusniveau. Vis man ønsker fortsat drilldown selvom mere end et kursus (topniveau) er valgt, så ændre HASONEFILTER til ISFILTERED.
```
Drill filter = IF(HASONEFILTER(Besvarelser[Kursusnavn]),"Hold","Kursus")
```
 
## Filter Measure på visualiseringerne 

```
VisualiseringDrill = IF(FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki])=[Drill filter],"Drill","Topniveau")

```
Dette measure sættes som filter på visualiseringen. 

FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki]) udvælger øverste række i hjælpetabellen

Filteret på visualiseringen bestemmer hvad der skal vises. Filteret er sat til

VisualiseringDrill IS NOT *Topniveau*

Fordi hjælpetabellen indeholder gentagende ID'er for hvert udsnit af hierarkiet, så vil kun det udsnit af tabellen hvor *placering i heiraki = Drill Filter* blive vist. Så hvis der ikke er valgt et filter, er Drill Filter falsk og navnet på topniveauet returneres og kun det vises. Hvis Drill filter var sand, så ville kun det nedre niveau vises. 

Så hvis der ikke er valgt et filter returnere Drill Filter *Kursus* og kun dette udsnit af hjælpetabellen indgår i visualiseringen 

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Kursus | Kursusnavn |
| 2 | Kursus |  Kursusnavn |

Havde man valgt et filter ville kun denne del af hjælpetabellen indgå i visualiseringen.

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Hold | Holdnavn |
| 2 | Hold |  Holdnavn |

For et udvidet eksempel, hvor hierarkiet har mere en to niveauer se. 
Kube measure 

*OrgNiveau* og 
*OrgNiveauFilterDrill*
 
