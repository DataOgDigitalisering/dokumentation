# Introduktion
Denne side beskriver de ting som man skal være opmærksom på når man bygger og arbejder med dashboards. Siden omhandler alt fra navngivning af bogmærker til best practice når man tiløjer filtre. Også mere avancerede ting som automatisk drill down på visualiseringer er beskrevet.

# Brugerstyring og sikkerhed

# navngivning af faner
# farver, tesktstørrelse, figurer - tag udgangpunkt i det der allerede er, kopier en figur f.eks.
# Filtre - på siden, på figuren, i mesuret 
# Selections
# Sync slicers
# Nulstil, Infoboks, vis filtervalg
# Filter på stilling og organisation



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
 
