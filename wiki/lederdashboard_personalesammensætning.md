# Personalesammensætning

## Lederdashboard

I dashboardet udstilles data på enkeltmedarbejderniveau tiltænkt ledere. 
Bruger får her overblik over udvalgte parametre om de medarbejdere, denne i forvejen har adgang til via PersonaleWeb. Se [***brugerstyring***](./data_brugerstyring).

Der filtreres globalt _på fanen_ ud fra kriterierne v_DimAnsættelse[AnsatDagsDato]=J og v_DimAnsættelse[AktuelRække]=J .
Som udgangspunkt vises altså alle lederens medarbejdere med en aktuel ansættelse pågældende dag inklusiv evt. tidligere (eller kommende) ansættelser på samme tjenestenummer.
Har bruger adgang til medarbejdere på tværs af organisationsstruktur, kan der filtreres herpå, ligesom der kan filtreres på tværs af stillingshieraki.
Foruden brug af grunddata er oprettet views og tabeller til brug i beregninger under dette tema. Se [***Resume af tabeller***](./data_personalesammensætning#resume-af-tabeller). 

<!-- Embed dashboards  -->
<!-- <details><summary markdown="span">HR Lederdashboard</summary>
<center> -->
<iframe src="https://flis.regionh.top.local:444/PBIReports/powerbi/L%C3%B8n%20og%20HR/HR%20Lederdashboard/Personalesammens%C3%A6tning?RC:Toolbar=false" style="border:1px #000000 solid;" frameborder="1" height="435" width="100%"></iframe>
<!-- </center>
</details> -->


#### Beregning

Measuret, _[Antal medarbejdere]_, summerer groft antallet af rækker i v_DimAnsættelse. Det anvendes i en række andre measures uden skelnen imellem populationer (månedslønnede, fuldtidsansatte eller andet). 
```DAX
[Antal medarbejdere] =
IF (
    ISBLANK ( COUNTROWS ( 'v_DimAnsættelse' ) ),
    0,
    COUNTROWS ( 'v_DimAnsættelse' )
)
```
Antallet af måneds- og timelønnede, fuld- og deltidsansatte, der fremgår af visninger (_cards_) til venstre i dashboardet, er alle baseret på _[Antal medarbejdere]_ evalueret i forskellige filterkontekster ved brug af én eller flere af de dikotomiserede J/N-kolonner i v_DimAnsættelse. Et eksempel herpå er _[Antal fuldtidsansatte]_
```DAX
[Antal fuldtidsansatte] =
CALCULATE (
    [Antal medarbejdere],
    'v_DimAnsættelse'[Månedslønnet] = "J",
    'v_DimAnsættelse'[Fuldtid] = "J"
)
```
   Antal _[Årsværk]_, vist sammen med de fire føromtalte, beregner summen af beskæftigelsesdecimaler, v_DimAnsættelse[Beskdec], som i definitionen er andelen af en 37 timers arbejdsuge, en person er ansat til og her i praksis oversættes til årsværk. Specifikt på visningen af årsværk filtreres v_DimAnsættelse[Månedslønnede]=’J’ i selve figuren.
```DAX
[Antal årsværk] =
// Kan kun bruges når man kigger på aktuelle ansættelser eller en bestemt dato
IF (
    ISBLANK ( SUM ( 'v_DimAnsættelse'[Beskdec] ) ), 
    0,
    SUM ( 'v_DimAnsættelse'[Beskdec] )
)
```
Til beregning af _[Ansættelseslængde]_ (antal år) anvendes differencen mellem dags dato og v_DimAnsættelse[Ansættelsesdato]. 
I figuren **Ansættelseslængde** anvendes dette measure af _[AnsatteAnsættelseslængdeInterval]_ til at beregne medarbejders ansættelseslængde i nuværende stilling (+evt tidligere ansættelser på samme tjenestenummer). Dette measure er designet til, i kontekst af v_TallyAnsættelseslænge, at beregne _[Ansættelseslængde]_ evalueret i en filterkontekst af tjenestenummer (og AnsættelsesID for at sikre optælling på unikke individer) og returnerer _antallet af medarbejdere i intervallerne_ specificeret i tally-tabellen.
Ved mouse-over vises den enkelte medarbejders ansættelseslængde udregnet med _[Ansættelseslængde]_.

Figuren **Aldersfordeling** viser antallet af medarbejdere, _[AnsatteAldersinterval]_, fordelt på aldersintervaller. Også dette measure er designet til visning i kontekst af en tally-tabel, v_TallyAlder. Metodisk er beregning og opbygning af measure identisk med førnævnte, _[AnsatteAnsættelseslængdeInterval]_, hvor der hér regners på alder i stedet for ansættelseslængde. Measuret, _[Alder]_, beregner blot en persons alder som differencen mellem dennes fødselsdag (v_DimPerson[Fødselsdato]) og dags dato. Specifikt på denne figur er nedre og øvre aldersintervaller filtreret fra via v_TallyAlder[AldersInterval_5år], så kun personer i alderen 15-79 år vises.
Ved mouse-over på **Aldersfordeling** vises enkelte medarbejderes _[Alder]_ inden for hvert interval

Tabellen **Hændelser 14 dg.** frem viser en kronologisk oversigt over udvalgte personrelaterede hændelser i de kommende 14 dage; fx fødselsdage, jubilæer, orlov, tiltrædelse, fratrædelse m.m. (Tabellen, **Hændelser 12 mdr. frem** via bogmærket af samme navn, er identisk med førnævnte men med filteret, v_DimTidDato[OffsetDato]=[0;365].

I **Informationstabel** vises udvalgte medarbejderdata herunder ansættelsessted (L6/L4, afsnit/afdeling), tjenestenummer, stilling, alder, ansættelseslængde, anciennitet m.m. _[Anciennitet]_ er hér ikke nødvendigvis lig _[Ansættelseslængde]_! Baseret på ansattes nuværende v_DimAnsættelse[Anciennitetsdato], kan denne dato ligge forud for ansættelse i Region H (ifm. tilskrivning af relevant anciennitet), eller den kan være ændret fx ifm. overflytning til anden overenskomst eller konvertering af deltidsenciennitet. Visse ansættelser med fastlåst anciennitetsforløb kan være uden anciennitetsdato. Measuret _[Anciennitet]_ beregner, i antal hele år, differencen mellem v_DimAnsættelse[Anciennitetsdato] og dags dato. For fremtidige anciennitetsdatoer anvendes dags dato.
_[Ansat til]_ angiver en eventuel slutdato på medarbejders senest tildelte tjenestenummer, hvis en sådan findes. _[Alder]_, _[Ansættelseslængde]_ og _[Årsværk]_ beregner, i kontekst af unikke personer (her i kontekst af kombinationen v_DimPerson[Navn] og v_DimAnsættelse[Tjnr]) pågældende persons alder og ansættelseslænge på dagen i hele antal år samt beskæftigelsesdecimal (årsværk) på pågældende ansættelse.




----------

## Strategisk Dashboard

<iframe src="https://flis.regionh.top.local:444/PBIReports/powerbi/L%C3%B8n%20og%20HR/HR%20Strategisk%20Dashboard/HR%20Strategisk%20Dashboard?RC:Toolbar=False" style="border:1px #000000 solid;" frameborder="1" height="435" width="100%"></iframe>



### Population

Alle visninger er baseret på beregningen, _[AntalAnsatteNedslagsdatoer]_. Denne er designet som et switch-measure til, i kontekst af valgt **Ansættelsesform**, at beregne enten _[Antal medarbejdere]_, _[Antal personer]_ eller _[Antal årsværk]_. 

I measuret er således defineret bereging og inklusionskriterier for summen af hver af populationerne; fuldtidsansatte, deltidsansatte, månedslønnede osv.

{::options parse_block_html="true" /}
<details><summary markdown="span">Measure: [AntalAnsatteNedslagsdatoer] </summary>
```DAX
-- fra [AntalAnsatteNedslagsdatoer] 
...
VAR __Ansaettelser =
    CALCULATE (
        [Antal medarbejdere],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Maanedsloennede =
    CALCULATE (
        [Antal medarbejdere],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[Månedslønnet] = "J",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Aarsvaerk =
    CALCULATE (
        [Antal årsværk],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[Månedslønnet] = "J",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Fuldtidsansatte =
    CALCULATE (
        [Antal medarbejdere],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[Månedslønnet] = "J",
        'v_DimAnsættelse'[Fuldtid] = "J",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Deltidsansatte =
    CALCULATE (
        [Antal medarbejdere],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[Månedslønnet] = "J",
        'v_DimAnsættelse'[Fuldtid] = "N",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Timeloennede =
    CALCULATE (
        [Antal medarbejdere],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[Ansat] = "J",
        'v_DimAnsættelse'[Månedslønnet] = "N",
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
VAR __Personer =
    CALCULATE (
        [Antal personer],
        'v_DimAnsættelse'[Start] <= __Dato, __Dato <= 'v_DimAnsættelse'[Slut],
        'v_DimAnsættelse'[EksterntFinansieret] <> __Filter_EksterntFinansierede
    )
...    
```
</details>
{::options parse_block_html="false" /}
    
 

### Udvikling over tid

Measuret [AntalAnsatteNedslagsdatoer] er også designet til at indgå i en kontekst af tid. 
```DAX
-- fra [AntalAnsatteNedslagsdatoer]
...
VAR __Dato = MAX( v_DimTidDato[Dato] )
VAR __ValgtAnsaettelsesform =
    SELECTEDVALUE ( v_TallyAnsaettelsesformer[Ansaettelsesform] )
...
```
I figurerne, der viser **udvikling i [...] fordelt på [..-grupper]**, filtreres direkte på figurerne med kriteriet v_DimTidDato[Nedslagsdatoer]={'1. dag i året', 'I dag'}. Det er samme beregning, der foretages, men vist i hoved-, fagstillings- og organisationskontekster. 

Til beregning af **Udvikling i antal måndeslønnede fordelt på hovedstillingsgrupper** vises desuden benchmarking mod tidligere nedslagsdatoer, 

$$ \frac{ antal_{\text{i dag}} - antal_{\text{nedslagsdato}} }{ antal_{\text{nedslagsdato}} } \cdot 100\% $$ 

Dette er implementeret i _[AendringIftBenchmark]_.
```DAX
[AendringIftBenchmark] =
//Measure beregner den procentvise ændring mellem to nedslagsdatoer (d.d. og benchmark)
VAR __AntalIdag = [AntalAnsatteDagsDato]
VAR __AntalBenchmark = [AntalAnsatteBenchmark]
VAR Result =
    IF ( __AntalIdag = 0 && __AntalBenchmark > 0,
        -1,
        DIVIDE ( __AntalIdag - __AntalBenchmark, __AntalBenchmark, 0 )
    )
RETURN Result
```
Her er _[AntalAnsatteBenchmark]_ og _[AntalAnsatteDagsDato]_ opbygget som swith-measures på samme måde som _[AntalAnsatteNedslagsdatoer]_. Det er på denne måde muligt at gøre benchmarkdatoen dynamisk ift. brugerinput.



### Fordeling på intervaller

Til **visning af månnedslønnede fordelt på [..-intervaller]** anvendes tre measures til beregning i hhv. alders-, anciennitets- og ansættelseslængdeintervaller. 

- _[AnsatteAldesintervalStrategisk]_
- _[AnsatteAnciennitetsinterStrategisk]_
- _[AnsatteAnsættelseslængdeintervalStrategisk]_

De tre measures er identiske i funktionen at aggregere og summere unikke individer (_[AntalAnsatteNedslagsdatoer]_) på intervaller defineret i **tally-tabellerne**: 

- v_TallyAlder
- v_TallyAnciennitet
- v_TallyAnsættelseslængde

> Tally-tabeller dannes med dét specifikke formål at kunne gruppere data på en ønsket måde. Vi definerer i disse tabeller bucketsize, intervalgrænser og -antal mhp. fx at gøre læsbarheden af grafer bedre.


# Personalesammensætning

<!-- ERD, datamodel -->
<details><summary markdown="span">Datamodel</summary>
     <center>
          **Udskiftes med ERD fra SSMS eller TE3**
          <img src="Images/erd/erd_pbi_personalesammensætning.png" height="95%" width="95%" class="center"/>
     </center>
</details>  
<br>


## Resume af tabeller

### v_DimHændelser

| **View** | **Opdateres** | **Baseret på** | 
| - | - | - |
| [chru_cube].[v_DimHændelser] | Dagligt | [DM_FL_HR].[DimHændelser] |

Udvalgte hændelser vedrørende en ansættelse. ID er primærnøgle.
Ved en hændelse forstås en af følgende mærkedage: dato for fødsels- og jubilæumsdag, til- og fratrædelser, flytter mellem afdelinger, termin samt orlov. 
Tabellen er niveaudelt i L1 og L2, hvor L2 er en uddybende tekst knyttet til den overordnede hændelse, L1; fx om ’Flytter afdeling’ er et skift _fra_- eller _til_ en afdeling. I kolonnen ’Note’ forklares, hvordan en hændelse er defineret—om den fx er direkte udledt vha. en dato, eller om der kigges på flere på hinanden følgende ansættelser og skift i statuskoder herimellem for at udlede, om en person går på eller kommer retur fra orlov.



### v_FactHændelser

| **View** | **Opdateres** | **Baseret på** | 
| - | - | - |
| [chru_cube].[v_FactHændelser] | Dagligt | [chru_cube].[v_DimAnsættelse] |
| | | [chru_cube].[v_Dimperson] |
| | | [chru_cube].[v_DimTidDato] |
| | | [DM_FL_HR].[FactTerminsdato] |

- Kan med fordel dokumenteres grundigere i script
- Vær opmærksom på, at HændelsesID hard-codes i overensstemmelse med definitioner i v_DimHændelser. Dvs. foretages modificeringer i v_DimHændelser, arves det ikke i fact-tabellen.
- Bemærk, at tabellen er koblet på v_SecurityOrganisationBridge via HændelseOrganisationID.

View er baseret på v_DimAnsættelser og beriges af øvrige tabeller. ID er primærnøgle. Historiske og fremtidige hændelser—nærmere defineret i v_DimHændelser—beregnes 13 måneder frem i tid for hvert år en aktuel medarbejder er ansat. Er hændelsen en fødsels- eller jubilæumsdag, er under ’AntalÅr’ anført hhv. personens alder det pågældende år, eller jubilæumslængde hvis det er et 1-, 5-, 10-, 15 (osv.) års jubilæum. 
Endeligt filtreres på hændelser i intervallet $$ \left[ -7\text{dage} ; 13\text{måneder} \right] $$. 

View er defineret i et længere script, der opsummeret udfører følgende step:
- Først sammensættes en temporær tabel, PersonBase, med rækker af fødsels- og jubilæumsdatoer _alle_ år i en persons ansættelsesperiode. 
- Dernæst en temporær tabel, PersonLags, med en række pr. ansættelse sammenfattende aktuelle samt evt. seneste og næstkommende ansættelsesforhold (OrganisationID og statuskode). 
- I en ny temporær tabel, MasterTable, listes for hvert tjenestenummer ’HændelsesID’ og tilsvarende ’HændelsesDato’. ’HændelsesID’ er her hard-codet i overensstemmelse med v_DimHændelser (1 for fødselsdag, 2 for jubilæum, 3 for tiltrædelse osv.). For ’HændelsesID’ svt. ’Fødselsdag’ og ’Jubilæumsdag’ anvendes allerede beregnede ’HændelsesDato’(er) fra PersonBase. Ved ’HændelsesID’er svt. til til- og fratrædelser samt flyt til- og fra afdeling anvendes nu PersonLags; 
     - På ’HændelsesID’ svt. ’Tiltræder’ defineres ’HændelsesDato’ som værende en ansættelses startdato på ansættelser, hvor ’Ansat’=J og dette er forskelligt fra en evt. umiddelbart foregående ansættelse på samme tjenestenummer; 
     - omvendt defineres ved ’HændelsesID’ svt. ’Fratræder’, at ’HændelsesDato’ er slutdatoen på en ansættelse, hvor ’Ansat’=N og dette er forskelligt fra en umiddelbart foregående ansættelse på samme tjenestenummer. 
     - Til ’HændelsesID’ svt. ’Skifter fra anden afdeling’ og ’Skifter til anden afdeling’ anvendes hhv. start- og slutdatoen på den ansættelse hvor ’OrganisationsID’ er forskelligt fra den umiddelbart forrige respektivt efterfølgende ansættelse. 
     - På ’HændelsesID’ svt. ’Går på orlov’ anvendes som ’HændelsesDato’ startdatoen på den ansættelse, hvor statuskode skifter til 3 og denne er forskellig fra foregående; 
     - For ’HændelsesID’ svt. ’Tilbage fra orlov’ anvendes omvendt ’HændelsesDato’ på ansættelsen hvor statuskode skifter fra 3 til 0 eller 1. 
     - På ’HændelsesID’ svt. termin anvendes som ’HændelsesDato’ ’Terminsdato’ fra tabellen [DM-FL-HR].[FactTerminsdato].
- Ovenstående beregninger samles i sidste temporære tabel, FinalTable, hvor tidssvarende ansættelses- og OrganisationsID tilføjes, relativ alder og jubilæumslængde beregnes og alt filtreres i tid, så kun hændelser i intervallet $$ \left[ -7\text{dage} ; 13\text{måneder} \right] $$ medtages. 
Endeligt tilføjes tidssvarende Stillings- og PersonID og rækker indekseres


<!-- ØVELSE -->
{::options parse_block_html="true" /}
<details><summary markdown="span">**ØVELSE - PERSONALESAMMENSÆTNING** <img src="Images/icons_ref/icon_git.png" height="35" width="35"></summary>

Beregn vha. kuben:
> - Hvor mange måneds- og timelønnede er ansat i sektionen dags dato med statuskode 0, 1 eller 3?
> - Hvor mange årsværk arbejdes i sektionen?
> - Hvordan er denne fordelingen mellem sektioner og jobstillinger?
> - Passer din udregning med hvad HR Lederdashboardet viser?
>
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_personale.sql" target="_blank">**løsningsforslag**</a>.

</details>
{::options parse_block_html="false" /}



### v_TallyAlder

| **View** | **Opdateres** |
| - | - |
| [chru_cube].[v_TallyAlder] | Dagligt / efter behov |

Talrækken 0-124 genereres og døbes ’Alder’. Næste to kolonner beregner placering af denne i 5- og 10 års intervaller døbt ’AldersInterval_5år’ og ’AldersInterval_10år’. Filtreres på alder fra 0-99 år.



### v_TallyAnciennitet

| **View** | **Opdateres** |
| - | - |
| [chru_cube].[v_TallyAnciennitet] | Dagtligt / efter behov |

Identisk i opbygning og beregninger som v_TallyAnsættelseslængde. 



### v_TallyAnsættelseslængde

| **View** | **Opdateres** | 
| - | - |
| [chru_cube].[v_TallyAnsættelseslængde] | Dagligt / efter behov |

Talrækken 0-124 genereres og døbes Ansættelseslængde’. Næste to kolonner beregner placering af denne i 5- og 10 års intervaller døbt ’AnsættelseslængdeInterval_5år’ og ’ AnsættelseslængdeInterval_10år’. Filtreres på ’ Ansættelseslængde’ fra 0-99 år. Til brug på fx figurakser, hvor kun et begrænset antal intervaller ønskes vist, beregnes kolonnen ’AnsættelseslængdeIntervalVisualisering’. 
Endeligt tilføjes ’AnsættelseslængdeIntervalVisualiseringSortering’ mhp. at kunne sortere forrige kolonne på dens ”numeriske” værdi i Power BI-visninger.




### v_TallyAnsættelsesform

| **View** | **Opdateres** |
| - | - |
| [chru_cube].[v_TallyAnsætelsesform] | Dagligt / efter behov |





