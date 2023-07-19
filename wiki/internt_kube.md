# Introduktion - UNDER UDVIKLING
Denne side beskriver de ting som man skal være opmærksom på når man bygger og arbejder med kuber.

# Kort om kuben
I dit arbejde får du brug for at kende og kunne arbejde med data i "**kuben**" (med kuben menes primært CHRU_HRKube). 

Både *HR Lederdashbord* og *HR Strategisk Dashboard* bygger på kuben. I kuben implementeres vores standardiserede beregningsmetoder indenfor temaer som sygefravær, ferieafholdelse, personalesammensætning, løn, vagtplan m.fl. 
Flere temaer tilføjes løbende i takt med efterspørgsel og tilgængelige datakilder, hvorfor vi altid bestræber os på, at kuben skal være en adaptiv størrelse. Hér er din indsigt i både muligheder og begrænsninger med den nuværende model værdifuld.

På produktions- og udviklingsserverne findes data under skemanavnet *chru_cube*. I Tabular Editor findes kuben under navnet *CHRU_HRKube*.

<details><summary markdown="span">Kuben pr. 2023-01-30</summary>
 Dette er er overbliksbillede på dagen over tabeller inkludert i kuben. Det er ikke fyldestgørende, men giver en ide om, hvordan tabeller tilføjes temavis i takt med, at vi løbende inkluderer flere datakilder.
 <center>
  <img src="Images/erd/erd_pbi_chru_hrkube_labels.png" height="480" width="800" onmouseover="CHRU_HRKube, 2023-01-30" style="vertical-align:middle"/>
 </center>
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={ae8fb223-d1a2-455d-9d7c-2e1a74aeb8ce}&amp;action=embedview&amp;wdAr=1.7777777777777777" height="480" width="800" frameborder="0"></iframe>
 </center>

 
</details>
<br> 

Som introduktion til kuben kan anbefales at gennemgå materialet hér på wiki-siden, ét tema ad gangen. Husk dog, at denne data er processeret til brug i datamodellen, hvorfor det er en nødvendighed, at du også har indblik i rådata fra fx Silkeborg Data (**SD**). 
Du kan med fordel prøve at bygge din egen kube i Tabular Editor. Dette kan give en god indsigt i hvordan *CHRU_HRKube* er bygget op.

Til hvert tema findes også små **øvelser**, hvor du kan testen din viden. Du vil herigennem få lidt erfaring med datatræk fra både rådata og kuben, og få indblik i nogle af de datatransformationer, som må foretages, før vi kan foretage beregninger og analyser.

# Brugerstyring og roller
Når man arbejder på en kube, er det vigtigt at man ved hvem der kan tilgå den. I dokumentationen af kuben er [brugerstyring](https://dataogdigitalisering.github.io/dokumentation/kube_brugerstyring) beskrevet. Her er det beskrevet hvordan vi benytter Row-Level Security (RLS) til at implementere brugerstyring på kuben. Ofte ønsker man dog først at lade folk tilgå en kube når den er færdigudviklet og klar til brug. Man kan se hvem der har adgang til en given kube ved tilgå kuben gennem *SQL Server Management Studio* (SSMS):
- Åben SSMS og forbind til den ønskede kube. Højreklik herefter på en af rollerne og vælg "*Properties*"
TODO BILLEDE ÅBEN ROLE
- Under "*Memebership*" kan du se hvem der har fået tildelt den givne rolle. Ofte ønsker vi kun at folk internt i *Data og Rapportering* skal kunne tilgå kuber som stadig er under udvikling. Når sikkerhed og brugerstyrring er testet igennem, kan man tildele eksterne folk i regionen rollen "*ReportReader*".
TODO BILLEDE ROLE SHOW MEMEBRS

I *Tabular Editor* kan man implementere brugerstyrring og RLS. Man skal dog være opmærksom på at alle som kan tilgå kuben også kan tilgå alle measures gennem DAX-Studio. Så man skal ikke skrive personfølsomme data ind i de measures som ligger i kuben.

# Arbejd med kuber
Når man laver ændringer i kuben er det vigtigt at *dokumenterer sit arbejde*. Dels skal man sørge for at komme *descriptions* på alle measures, tabeller og kolonner. Men man skal også huske at opdaterer dokumnetationen på vores Wiki-side, så den ikke bliver uddateret. Dette er beskrevet i afsnittet om [*dokumentering*](https://dataogdigitalisering.github.io/dokumentation/internt_dokumentering). 

Herudover benytter vi GitHub til *versionsstyring af vores kuber*. På denne måde kan vi let arbejde parallelt på den samme kube, og *merge* vores ændringer sammen. Hvis man laver ændringer i en kube, eller vil lave en ny kube, er det vigtigt at man benytter versionsstyring fra starten. Man kan læse mere om dette under [*versionsstyring*](https://dataogdigitalisering.github.io/dokumentation/internt_versionsstyring)

Nedenfor er det beskrevet hvordan vi navngiver og opbygger vores kuber. Ved at følge disse konventioner, sikrer vi os at kubens opbygning er konsistent på tværs af temaer og emner.

# Tabeller og relationer
navn, definition, parititioner, kolonner, navn, type, format, sort by  navngivning, secutirycorssfiltering, 

## Intro til tabellerne
I grove træk falder al data i kuben indenfor kategorierne

| **Grunddata** | **Temaespecifik data** | **Hjælpetabeller** | **Infotabeller** |
 
- Med **grunddata** menes den data, som er fællesmængde på tværs af temaer, uanset om der beregnes på sygefravær, ferieafholdelse eller andet. I grunddata indgår:
  - **Stamdata** er personaledata, organisations-, stillings- og lønarthieraki, tidstabel mm. 
  - **Brugerstyring** er data om personales brugerroller, som er bestemmende for hvilke data, brugere af vores produkter må se. Det er essentielt at forstå, [hvordan brugerstyring er implementeret](./kube_brugerstyring) for at sikre, at denne også virker på tilføjelser i kuben. 
- **Temaspecifik data** anvendes specifikt til beregning på fx sygefravær, ferieafholdelse eller personalesammensætning. Af screenshottet herover ses, hvordan vores data groft er grupperet i temaer.

Derudover findes en række øvrige tabeller, herunder:
- Hjælpetabeller er **tally**- og **slicer**-tabeller. Disse bruges til definereing af intervaller (fx aldersintervaller), grupperings-, sorterings- og filtreringsmuligheder
- Info er data som fx dato på **dataleverancer** og **servicemeddelelser** til brugere af dashboard om nye opdateringer eller tilføjelser

## Navngivning af tabeller
- Navngives som fx v_DimAnsættelse
- Skabelon: [tabeltype]+[\_]+[Formål]+[BeskrivendeNavn]
- **Views** indledes med __v\___ 
  - Alt *efterfølgende* skrives i camelCase (**S**tort**B**egyndelsesbogstav)
  - **Formål**: Dim, Fact, Security, Info, Slicer, Tally.
  - **Beskrivende navn** er entydig(e) og letforståelig(e) *substantiv(er)*. (Gerne noget der minder om rådatatabellens oprindelige navn hvis viewet er baseret på en sådan). Sammensatte ord skrives i camelCase

- **Kolonnenavne** er entydige og letforståelige *substantiver*
  - camelCase
  - Disse felter udfyldes i Tabular Editor, hvis ikke de er pre-udfyldt:
    - Data Type
    - Description
    - Key

  - Undgå så vidt muligt datatransformation i Tabular Editor. Det giver bedre overblik at have samlet i SQL.

# Measures
navn, mappe, Opbygning, __foran variabel?, format, type, 
### Intro til measures
Via measures implementeres vores standardiserede beregningsmetoder. De er grupperet temavis. I gruppen \__Diverse_ indgår beregninger på stamdata og dette kan være et godt sted at starte med at skabe overblik over kuben. Foruden indblik i de mere centrale tabeller vil du hér se eksempler på, hvordan viden om stamdata er essentielt for at kunne definere fx hvilken personalegruppe, der skal indgå i en given beregning; hvordan dette kan variere fra tema til tema; hvordan antallet af personer, der indgår i en beregning, er afgørende for, om et resultat nødvendigvis skal anonymiseres mm.

Andre measures—lokaliseret i mapperne, \__Farver_ og \__Tekster_—bruges til kontrol af layout på dashboards; Farvetemaer, dynamiske akselængder og tekstetiketter, meddelelser, kolonnebredder mm. 


### Navngivning af measures
- Navngives fx [Fravær - vægtede fuldtidsfraværsdage]. 
- Skabelon: [tema - beskrivende og letforståelig tekst]
  - (ikke nødvendigvis camelCase)
- Measures grupperes i temaspecifikke mapper
  - Enkelte basis-measures placeres i mappen _Diverse_, hvis de bruges på tværs af temaer. Fx [Antal fuldtidsansatte] og [FilterSlicer]
- æ ø å tilladt
- Ikke alle measures er navngivet efter denne konvention. Ved tvivl se mappen _Sygefravær_
- Disse felter udfyldes i Tabular Editor, hvis ikke de er pre-udfyldt:
  - Description
<br>


