# Introduktion - UNDER UDVIKLING
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
Alle objekter som figurer, knapper og tekstfelter skal grupperes. Dette gør det f.eks. lettere at holde styr på layer order og bogmærker. Under fanen "View" i Power BI kan man vælge at få "*Selection*" vist. Det vigtigste er at man har de fire grupperinger:
 - "*Info*" - hvor alle objekter og tekstbokse som bliver vist i infoboksen er med.
 - "*Generelt*" - hvor overskift, logo og tekst som beskriver opdateringskadancen er med.
 - "*Filtre*" - som indeholder alle slicers, bokse mm. som danner filtrene i højre side af dashboardet.
<br><img src="Images/BillederInterntDashboard/selections.PNG" height="230" style="vertical-align:middle"/>

Herudover er det ofte en god idé at gruppere figurer og visualiseringer. Man skal være opmærksom på at rækkefølgen på objekterne i "Selection" styrer deres layer order. **Det er også en god idé at slå  "*Maintain Layer order*" til på alle figurer og knapper**, så de ikke "bytter" plads når man klikker på dem i det færdige dashboard.
<br><img src="Images/BillederInterntDashboard/layerOrder.PNG" height="250" style="vertical-align:middle"/>

# Formatering af figurer og tekster
Dashboardsne benytter bestemte farver, skrifttyper, skriftstørelser osv. Nogle af disse farvekoder er gemt i kuben under "*_Farver*" og kan refereres til gennem Power BI. Andre er tastet manuelt ind på den givne figur. **Det er ofte en god idé at kopiere en figur som allerede er i dashboardet** og tage udgangspunkt i denne. På den måde sikrer man sig at skrifttype, skriftstørelse mm. er identiske. Overskrifter skriver man normalt ind manuelt med mindre den optræder flere steder eller skal være dynamisk. Hvis overskfiten skal være dynamisk kan man gemme den i kuben under "*_Tekster*".

# Filtre - på siden, på figuren, i measuret
Filterering af data kan ske direkte i measuret eller det kan ske i Power BI. Ofte er det en god idé at lave nogle measures som er lidt mere generelle, men tilføje filtrene i Power BI. Dette er dog ikke altid muligt eller hensigtsmæssigt, og vi har ikke en fast regel for hvor et filter skal tilføjes. I Power BI kan man tilføje filtre på hele siden. Disse filtre vil være forskellige for hvert temae, da vi ikke har én standardpopulation som går igen i alle temaer og dashboards. Herudover kan man tilføje filtre på den enkelte figur. På den enkelte figur kan man også vælge eller fravælge funktionen "*Shot items with no data". Dette kan hjælpe med at frasortere uinteressante afsnit og stillinger uden data eller ansatte.

# Anonymsering
I det strategiske dashboard skal man være opmærksom på at alle visninger skal være anonymiseret korrekt. Man kan implementere anonymiseringen på flere måder. Dels kan man gøre det direkte i measuret, ved at sige den skal returnere værdien "BLANK()" hvis man er kommet under anonymitetsgrænsen. Man kan også lave et measure som tæller antal besvarelser og bruge dette i sit filter, ved f.eks. at sige antal besvarelse skal være større end eller lig 5. Det er op til en selv hvilken metode man synes er mest hensigsmæssig, men for at undgå for mange measures i kuben, kan det være hensigtsmæssigt at implementere anonymsieringen gennem et filter på den give figur i Power BI.

# Filter på stilling og organisation
Tabellerne "*v_DimOrganisation*" og "*v_DimStilling*" indholder både aktive og inaktive afsnit og stillinger. Dette kan være brugbart når man kigger tilbage i tiden, da man herved ikke "overser" nogle lukkede afsnit eller stillinger. Det kan dog være uhensigtsmæssigt at vise afsnit og stillinger, som ikke har nogle rækker i "v_DimAnsættelse", da der ikke er noget data på disse. Vi har ikke en konsistent måde at filtrere afsnit og stillinger. Til at filtrere afsnit kan man dog benytte kolonnen "MedarbejdereAnsat", som har værdien "1" hvis der findes rækker i "v_DimAnsættelse" som knytter sig til det givne afsnit, og eller har den væriden "0". Stilling har ikke en tilsvarende kolonne, men kan man vælge at frasoretere blanke rækker. Dette er et udviklingspunkt hvor vi skal finde en mere konsistent måde at filtrere "uinteressante" afsnit og stillinger fra.

# Sync slicers
De slicers som ligger i højre side af dashboardet og går igen henover flere temaer skal synkroniseres korrekt. Under fanen "*View*" kan man vælge at se "*Sync Slicers*", herefter kan man vælge en given slicer og sikre sig at den bliver vist og virker på alle de ønskede sider som f.eks. siderne med filtervalg.

# Bogmærker
Bogmærker bruges bla. til at nulstille filtreringerne og vise infobokse. Alle bogmærker er grupperet under det tema som de tilhører. Alle bogmærker virker som udgangspunkt på alle figurer og objekter på en given side. Hvert tema har som udgangspunkt tre bogmærker, f.eks. har trivsel følgende:
- "*Trivsel - Nulstil*" som virker på alle figurer og også på "*Data*" hvilket vil sige at den styre de filtreringer man har valgt i slicerne og de filtre man har tilføjet til siden og figurerne. **Man skal huske at opdatere dette bogmærke hver gang man ændre filtrene på en figur**, ellers "overskriver" man filtrene når man klikker på bogmærket. Dette bogmærke bruges til "*Nulstil*"-knappen. 
- "*Trivsel*" virker på alle figurer, men ikke på "*Data*", den påvirker derfor ikke filtrevalgene. Det bruges til at lukke infoboksen.
- "*Trivsel Info*" virker på alle figurer, men ikke på "*Data*", den påvirker derfor ikke filtrevalgene. Det bruges til at åbne infoboksen.
Nogle gange er der behov for flere bogmærker, dette er f.eks. tilfældet hvis man vil vise figurer på tværs af organisiation og stilling vha. knapper. Dette kan ses i temaet "*Exit-undersøgelse*" i HR Strategisk Dashboard.
Da bogmærker let kan overskrive filtre på figurer er det vigtigt at man har dokumenteret sine filtreringer her på vores Wiki-side, så man kan genskabe visualiseringerne, hvis det skulle blive nødvendigt. En sidste ting man skal være opmæskom på er at slicerne i højre skal sættes op så ingen felter er valgt på forhånd. Dette skal gøres manuelt, og man skal sikre sig at det er tilfældet hver gang man gemmer. Bogmærker kan ikke styre dette.
<br><img src="Images/BillederInterntDashboard/SlicerSettingIngenValgt.PNG" height="250" style="vertical-align:middle"/>

# Nulstil, Infoboks, vis filtervalg
Der er tre vigtige knapper som går igen i alle temaerne, det er
- "*Nulstil*" - Denne knap nulstiller alle filtre. Husk at opdater den hver gang du ændrer filtrene på dine figurer.
- "*Infoboksen*" - Her er alle visualiseringerne beskrevet. Sørg for at figureren, tallene og teksten er grupperet korrekt. Se evt. siden "*Exit-undersøgelse*" i HR Strategisk Dashboard.
-  "*Infoboksen*" - Her kan brugeren få et overblik over de filtreringer man har valgt i slicerne i højre side. Se evt. siden "*Exit-undersøgelse*" i HR Strategisk Dashboard for opsætning og layout.


# Automatisk drilldown på visualiseringer
Nogle gange ønsker man at en visualisering automatisk viser et lavere nivaeu når man filtrere på afdelinger eller stillinger. Det beskrives her hvordan man på hierarkisk struktureret data, automatisk kan få vist det nedre niveau, når man har filtreret på det øvre niveau. I temaet "*Exit-undersøgelse*" I HR Strategisk Dashboard kan man se det blive brugt med organisationsstrukturen. Power BI understøtter desværre ikke denne funktion som standard, men ved brug af en hjælpetabel, to measures og et filter på visualisering, kan funktionen opnås.

## Hjælpetabellen
Det er nødvendigt at have en hjælpetabel, som indeholder det fulde heiraki. Her ses et eksempel på hjælpetabellens struktur fra kursusportal dashboard:

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Kursus | Kursusnavn |
| 2 | Kursus |  Kursusnavn |
| 1 | Hold | Holdnavn |
| 2 | Hold |  Holdnavn |

Den indeholder to kurser med ID'erne 1 og 2, og hvert kursus optræder to gange. En gang hvor man har inkluderet kursusnavnet, og en gang hvor man inkluderet holdnavnet. Se evt. tabellen "*v_DimOrgDrill*" i kuben for et eksempel med flere niveauer.

Tabellen er opbygget som Union hvor ID'erne gentages for hvert niveau. Tabellen tilføjes til resten af datamodellen via enten en begge vejet mange til mange relation eller ved brug af en bridge tabel.  
## Bestem aktivt niveau i hierarkiet
Man skal herefter fortælle Power BI hvilke rækker i hjælpetabellen som skal vises, da vi ikke ønsker at vise kurser og hold på samme tid! Dette kan gøres med et measure af typen:

```
Drill filter = IF(HASONEFILTER(Besvarelser[Kursusnavn]),"Hold","Kursus")
```

Her ses hvordan det fungere for kursusportalen. Et kursus kan have flere hold og vi ønsker at visualiseringen skifter til hold-niveau, når man har valgt et bestemt kursus med sliceren. Vis man vælger flere kurser, vises visualiseringen på kursusniveau. Vis man ønsker fortsat drilldown selvom mere end et kursus (topniveau) er valgt, så skal man ændre HASONEFILTER til ISFILTERED:
 
## Filter Measure på visualiseringerne 
Herefter skal man benytte sit measure til at filtrere visualiseringen i Power BI. Dette kan gøres ved at definere et measure af tyoe:
```
VisualiseringDrill = IF(FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki])=[Drill filter],"Vis","VisIkke")

```
Dette measure sættes som filter på visualiseringen. 

FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki]) udvælger øverste række i hjælpetabellen

Filteret på visualiseringen bestemmer hvad der skal vises. Filteret er sat til

VisualiseringDrill IS NOT *VisIkke*.

Fordi hjælpetabellen indeholder gentagende ID'er for hvert udsnit af hierarkiet, så vil kun det udsnit af tabellen hvor *Hjælpetabel[Placering i heiraki]=[Drill filter]* blive vist. Så hvis der ikke er valgt et filter, er *[Drill Filter] = "Kursus"* og kun de rækker med "*Kursus*" i kolonnen "*Hjælpetabel[Placering i heiraki]*" vises. Hvis "*HASONEFILTER(Besvarelser[Kursusnavn])*" var sandt, så ville kun det nedre niveau, "*Hold*" som blev vist. 

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
 
