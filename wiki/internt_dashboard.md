# Introduktion
Denne side beskriver de ting som man skal være opmærksom på når man bygger og arbejder med dashboards. Siden omhandler alt fra navngivning af bogmærker til best practice når man tilføjer filtre. Også mere avancerede ting som automatisk drill down på visualiseringer er beskrevet. Vi arbejder med dashboards i programmet *Power BI Desktop* som kan downloades via. *Softwareshoppen*.

# Brugerstyring og sikkerhed
Man kan dele sit dashboard med andre ved at lægge det op på FLIS. Her skal man dog være opmærksom på hvem der kan tilgå dashboardet. Man kan se hvem der har adgang til filen ved at klikke på "*...*" til højre for filen, vælge "*Manage*" og herefter klikke på "*Security*". Nogle personer bliver automatisk tilføjet som læsere når man uploader en Power BI fil til serveren. Det er derfor vigtigt, at man altid tjekker hvem der har adgang til at tilgå dashboardet, efter man har uploadet sin fil. Under "*Manage*" kan man også sætte en systembruger op, hvis det er nødvendigt.
<br><img src="Images/BillederInterntDashboard/SikkerhedFlisFil.png" height="80" style="vertical-align:middle"/>
<br>

På siden [*Tabeller og versionsstyring*](https://dataogdigitalisering.github.io/dokumentation/internt_tabellerOgDatabaser) kan du få et overblik over vores databaser og de tilhørende rapport-servere.

# Navngivning af faner
Fanerne i dashboardet navngives på følgende måde:
- Den centrale side for et givent tema kalder man bare temaets navn, f.eks. "*Trivsel*"
- Undersider til det givne tema navngiver man "*SUB*", f.eks. "*SUB - Organisationsherakisk*".
- Siden med filtervalg navngiver man "*FV*", f.eks. "*FV - Trivsel*"
- Siden med tooltips navngiver man "*TT*", f.eks. "*TT - Trivsel - Hovedstillingsgruppe*".

Rækkefølgen på fanerne er også vigtig. Alle temaer og deres tilhørende undersider kommer først. Herefter kommer alle sider med filtervalg, og til sidst kommer alle sider med tooltips. Dette kan f.eks. ses i HR Strategisk Dashboard.
# Selection - gruppering af objekter
Alle objekter som figurer, knapper og tekstfelter skal grupperes. Dette gør det lettere at holde styr på layer order og bogmærker. Under fanen "*View*" i Power BI kan man vælge at få "*Selection*" vist. Vi inddeler objekterne i følgende grupperinger:
 - "*Info*" - hvor alle objekter og tekstbokse, som bliver vist i infoboksen, er med.
 - "*Generelt*" - hvor overskrift, logo og tekst som beskriver opdateringskadencen er med.
 - "*Filtre*" - som indeholder alle slicers, bokse mm. som danner filtrene i højre side af dashboardet.
<br><img src="Images/BillederInterntDashboard/selections.PNG" height="240" style="vertical-align:middle"/>

Herudover er det ofte en god idé at gruppere grafer og visualiseringer. Man skal være opmærksom på at rækkefølgen af objekterne i "*Selection*" styrer deres layer order. **Det er også en god idé at slå  "*Maintain Layer order*" til på alle figurer og knapper**, så de ikke "bytter plads" når man klikker på dem i det færdige dashboard:
<br><img src="Images/BillederInterntDashboard/layerOrder.PNG" height="260" style="vertical-align:middle"/>

# Formatering af figurer og tekster
Vi benytter bestemte farver, skrifttyper og skriftstørrelser i vores dashboards. Nogle farvekoder er gemt i kuben under "*_Farver*" og kan refereres til gennem *Power BI*. Andre er tastet manuelt ind på den givne figur. **Det er ofte en god idé at kopiere en figur som allerede er i dashboardet** og tage udgangspunkt i den, når man vil tilføje nye figurer. På den måde sikrer man sig at skrifttype og skriftstørrelser mm. er identiske. Man skriver normalt overskrifter og tekster ind manuelt i *Power BI*, medmindre de optræder flere steder eller skal være dynamisk. Hvis overskriften skal være dynamisk, kan man gemme den i kuben under "*_Tekster*".

# Filtre - på siden, på figuren og i measuret
Filtrering af data kan ske direkte i measuret eller det kan ske i *Power BI*. Ofte er det en god idé at lave nogle measures som er lidt mere generelle, og herefter tilføje filtrene i *Power BI*. Dette er dog ikke altid muligt eller hensigtsmæssigt, og vi har ikke en fast regel for hvor et filter skal tilføjes. I *Power BI* kan man tilføje filtre på hele siden. Disse filtre er ofte forskellige for hvert tema, da vi ikke har én standardpopulation som går igen på tværs af alle temaer og dashboards. Herudover kan man tilføje filtre på den enkelte figur. På den enkelte figur kan man også vælge eller fravælge funktionen "*Show items with no data*". Dette kan hjælpe med at frasortere uinteressante afsnit og stillinger som ikke har noget data eller ansatte tilknyttet sig.
<br><img src="Images/BillederInterntDashboard/showNoData.png" style="vertical-align:middle"/>

# Anonymisering
I *HR Strategisk Dashboard* skal man være opmærksom på at alle visninger skal være anonymiseret korrekt. Man kan implementere anonymiseringen på flere måder. Dels kan man gøre det direkte i measuret, ved at sige den skal returnere værdien "*BLANK()*" hvis antallet af personer eller besvarelser som man kigger på er under anonymitetsgrænsen. Man kan også lave et measure som tæller antal personer og bruge dette i sit filter på figuren, ved fx at sige antal af personer skal være større end eller lig 5. Det er op til en selv hvilken metode man synes er mest hensigtsmæssig, men for at undgå for mange measures i kuben, kan det være en fordel at implementere anonymiseringen gennem et filter på den givne figur i *Power BI*.

# Filter på stilling og organisation
Tabellerne "*v_DimOrganisation*" og "*v_DimStilling*" indeholder både aktive og inaktive afsnit og stillinger. Dette kan være brugbart når man kigger tilbage i tiden, da man herved ikke overser nogle lukkede afsnit eller stillinger. Det kan dog være uhensigtsmæssigt at vise afsnit og stillinger, som ikke har nogle tilhørende rækker i *"v_DimAnsættelse"*, da der ikke er noget data på disse. Vi har ikke en konsistent måde at filtrere disse afsnit og stillinger fra. **Dette er et udviklingspunkt, hvor vi skal finde en mere konsistent måde at filtrere de uinteressante afsnit og stillinger fra**.

# Sync slicers
De slicers som ligger i højre side af dashboardet og går igen henover flere temaer skal synkroniseres korrekt. Under fanen "*View*" kan man vælge at vise "*Sync Slicers*". Herefter kan man vælge en given slicer og sikre sig at den bliver vist og virker på alle de ønskede sider som fx siderne med filtervalg.
<br><img src="Images/BillederInterntDashboard/SyncSlicer.png" height="150" style="vertical-align:middle"/>

# Bogmærker
Bogmærker bruges bl.a. til at nulstille filtreringerne og vise infoboksene. Alle bogmærker er grupperet efter det tema som de knytter sig til, og de skal virke på alle figurer og objekter på den givne side. Hvert tema har som udgangspunkt tre bogmærker, fx har trivsel følgende:
- "*Trivsel - Nulstil*" som virker på alle figurer og også på "*Data*", hvilket vil sige at den styre de filtreringer man har valgt i slicerne og de filtre man har tilføjet til siden og figurerne. **Man skal huske at opdatere dette bogmærke hver gang man ændrer filtrene på en figur**, ellers "overskriver" man sine filtre når man klikker på bogmærket. Dette bogmærke bruges til *Nulstil-knappen*.
- "*Trivsel*" virker på alle figurer, men ikke på "*Data*", den påvirker derfor ikke filtervalgene. Det bruges til at lukke infoboksen.
- "*Trivsel Info*" virker på alle figurer, men ikke på "*Data*", den påvirker derfor ikke filtervalgene. Den bruges til at åbne infoboksen.
<br><img src="Images/BillederInterntDashboard/bogmærkerTrivse.png" height="240" style="vertical-align:middle"/>


Nogle gange er der behov for flere bogmærker, dette er f.eks. tilfældet hvis man vil vise figurer på tværs af organisation og stilling vha. knapper. Dette kan ses i temaet "*Exit-undersøgelse*" i HR Strategisk Dashboard. Da bogmærker let kan overskrive filtre på figurer, er det vigtigt at man har dokumenteret sine filtreringer her på vores Wiki-side, så man kan genskabe visualiseringerne, hvis det skulle blive nødvendigt. 


En sidste ting man skal være opmærksom på, er at slicerne i højre side skal sættes op så ingen felter er valgt på forhånd. Dette skal gøres manuelt, og man skal sikre sig at det er tilfældet hver gang man gemmer. Bogmærker kan ikke styre dette:
<br><img src="Images/BillederInterntDashboard/SlicerSettingIngenValgt.PNG" height="250" style="vertical-align:middle"/>

# Nulstil, Infoboks og vis filtervalg
Der er tre vigtige knapper som går igen i alle temaerne, det er
- "*Nulstil*" - Denne knap nulstiller alle filtre. Husk at opdatere det tilhørende bogmærke hver gang du ændrer filtrene på dine figurer.
- "*Infoboksen*" - Her er alle visualiseringerne beskrevet. Sørg for at cirklerne, tallene og teksten er grupperet korrekt. Se evt. siden *Exit-undersøgelse* i HR Strategisk Dashboard.
-  "*Vis filtervalg*" - Her kan brugeren få et overblik over de filtreringer man har valgt i slicerne i højre side. Se evt. siden "*Exit-undersøgelse*" i HR Strategisk Dashboard for opsætning og layout.

# Automatisk drilldown på visualiseringer
Nogle gange ønsker man at en visualisering automatisk viser et lavere niveau, når man fx filtrerer på afdelinger eller stillinger. Det beskrives her hvordan man på hierarkisk struktureret data, automatisk kan få vist det nedre niveau, når man har filtreret på det øvre niveau. I temaet "*Exit-undersøgelse*" i HR Strategisk Dashboard kan man se det blive brugt med organisationsstrukturen i en figur med liggende søjler. *Power BI* understøtter desværre ikke denne funktion som standard, men ved brug af en hjælpetabel, to measures og et filter på visualisering, kan funktionen opnås.

## Hjælpetabellen
Det er nødvendigt at have en hjælpetabel, som indeholder det fulde heiraki. Her ses et eksempel på hjælpetabellens struktur fra kursusportal dashboardet:

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Kursus | Kursusnavn |
| 2 | Kursus |  Kursusnavn |
| 1 | Hold | Holdnavn |
| 2 | Hold |  Holdnavn |

Den indeholder to kurser med ID'erne 1 og 2, og hvert kursus optræder to gange. En gang hvor man har inkluderet kursusnavnet, og en gang hvor man inkluderet holdnavnet. Se evt. tabellen *v_DimOrgDrill* i kuben for et eksempel med flere niveauer.

Tabellen er opbygget som Union hvor ID'erne gentages for hvert niveau. Tabellen tilføjes til resten af datamodellen via enten en begge vejet mange til mange relation eller ved brug af en bridge tabel.  

## Bestem aktivt niveau i hierarkiet
Man skal herefter fortælle Power BI hvilke rækker i hjælpetabellen som skal vises, da vi ikke ønsker at vise kurser og hold på samme tid. Dette kan gøres med et measure af typen:

```
Drill filter = IF(HASONEFILTER(Besvarelser[Kursusnavn]),"Hold","Kursus")
```

Her ses hvordan det fungerer for kursusportalen. Et kursus kan have flere hold og vi ønsker at visualiseringen skifter til hold-niveau, når man har valgt et bestemt kursus med sliceren. Dvs. vi går fra at vise hvert kursus som en liggende søjle, til at vise hvert hold. Hvis man vælger flere kurser, vises visualiseringen på kursusniveau. Vis man ønsker fortsat drilldown selvom mere end et kursus (topniveau) er valgt, så skal man ændre HASONEFILTER til ISFILTERED.
 
## Benyt filter på visualiseringerne 
Herefter skal man benytte sit measure til at filtrere visualiseringen i Power BI. Dette kan gøres ved at definere et measure af typen:
```
VisualiseringDrill = IF(FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki])=[Drill filter],"Vis","VisIkke")
```
hvor "FIRSTNONBLANK(Hjælpetabel[Placering i heiraki],Hjælpetabel[Placering i heiraki])" udvælger øverste række i hjælpetabellen. Herefter sættes filteret på visualiseringen i *Power BI* til 
```
VisualiseringDrill IS "Vis"
```

Fordi hjælpetabellen indeholder gentagende ID'er for hvert udsnit af hierarkiet, vil kun det udsnit af tabellen hvor *Hjælpetabel[Placering i heiraki]=[Drill filter]* blive vist. Så hvis der ikke er valgt et filter, er *[Drill Filter] = "Kursus"* og kun de rækker med "*Kursus*" i kolonnen "*Hjælpetabel[Placering i heiraki]*" vil blive vist. Hvis "*HASONEFILTER(Besvarelser[Kursusnavn])*" derimod var sandt, så er det kun det nedre niveau, "*Hold*", som bliver vist.

Så hvis der ikke er valgt et filter, returnerer measuret *Drill Filter* værdien *Kursus*, og følgende udsnit af hjælpetabellen indgår i visualiseringen: 

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Kursus | Kursusnavn |
| 2 | Kursus |  Kursusnavn |

Havde man derimod valgt ét bestemt kursus, ville kun denne del af hjælpetabellen indgå i visualiseringen:

| ID |  Placering i heiraki |Navn |
| ----------- | ----------- | ----------- |
| 1 | Hold | Holdnavn |
| 2 | Hold |  Holdnavn |

For et udvidet eksempel, hvor hierarkiet har mere en to niveauer, kan du se de to measures *OrgNiveau* og *OrgNiveauFilterDrill* som fanen "*Exit-undersøgelse*" i HR Strategisk Dashboard benytter.
 
