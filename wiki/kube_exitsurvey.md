# Introduktion til temaet
ExitSurvey (også kaldet Exit-undersøgelse) er et tema i HR Strategisk Dashboard. Nedenstående beskriver de tabeller, kolonner og measures i CHRU_HRKube som knytter sig til temaet. Under fanen "HR Strategisk Dashboard" i sidemenuen kan du læse mere om de figurer som optræder i dashboardet.

# Tabeller og kolonner
Nedenfor er tabeller, kolonner og relationer beskrevet. Der er også blevet trukket noget metadata fra CHRU_HRKube'n i produktion, dette kan ses i de vedhæftede Excel-filer.

## Oversigt over tabeller og kolonner
<details><summary markdown="span">Oversigt over kuben</summary>
 
<b>Tabeller</b>
<center>
<iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="100%" height="500" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>

<b>Relationer</b>
<center>
<iframe width="100%" height="150" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Relationer&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>  
<br>

## v_FactExitSurvey
**Bygger på følgende views**:
- [v_FactExitSurvey](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_FactExitSurvey.sql)

**Ekstra informationer om tabellen**:
- Selvom tabellen bliver processeret dagligt, bliver data kun indlæst én gang om måneden og går pt. kun ét år tilbage. Dette er sikret ved at benytte følgende where-clause (leverancedato er en dato som SurveyXact opgiver):
```sql
WHERE ...
    AND Leverancedato < DATEFROMPARTS(YEAR(GETDATE()),MONTH(GETDATE()),1)
    AND Leverancedato >= DATEFROMPARTS(YEAR(GETDATE())-1,MONTH(GETDATE()),1)
```
- Tabellen indeholder kun svar fra gennemførte surveys, og hvis en person ved en fejl har fået tilsendt flere surveys til samme tjenestenummer vælges det først besvarede survey ud.
- Mange af spørgsmåls- og svarteksterne er hard-coded i viewet. Man skal derfor altid tjekke viewet efter, hvis der bliver ændret i surveyets ordlyd, temaer, svarmuligheder mm.

## v_DimExitSurveyRespondent
**Bygger på følgende views**:
- [link til view fra denne folder](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_DimExitSurveyRespondent.sql)

**Ekstra informationer om tabellen**:
- vigtige tanker/overvejelser ved dannelsen af tabellen
- vigtige tanker/overvejelser ved afgrænsning af data
- Hvornår/hvordan opdateres den - skal den opdateres manuelt nogle gange (f.eks. hvis der er nogle værdier som er hard-coded ind el.lign.)
- Andet

**Ekstra informationer om kolonnerne**:
- vigtige tanker/overvejelser ved dannelsen af kolonner
- vigtige tanker/overvejelser ved afgrænsning af data
- Andet

## v_TallyAmbassadør
**Bygger på følgende views**:
- [link til view fra denne folder](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_TallyAmbassad%C3%B8r.sql)

**Ekstra informationer om tabellen**:
- vigtige tanker/overvejelser ved dannelsen af tabellen
- vigtige tanker/overvejelser ved afgrænsning af data
- Hvornår/hvordan opdateres den - skal den opdateres manuelt nogle gange (f.eks. hvis der er nogle værdier som er hard-coded ind el.lign.)
- Andet

**Ekstra informationer om kolonnerne**:
- vigtige tanker/overvejelser ved dannelsen af kolonner
- vigtige tanker/overvejelser ved afgrænsning af data
- Andet


# Measures
Her er de measures som knytter sig til temaet Exit-undersøgelse beskrevet. Nogle measures har også en mere uddybende tekst.

## Oversigt over measures
<details><summary markdown="span">Oversigt over measures</summary>
 
<b>Measures</b>
<center>
<iframe width="100%" height="800" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>  

## Exit - AntalBesvarelser
- Inputværdier:
  - Ingen
- Returværdier:
  - anonymitetsgrænse
- Uddybende bemærkninger:
  - Denne værdi følger den som også gælder for trivselsdata.

Vigtige informationer om measure’et. Hvad er dens funktion, hvordan bruges den, vigtige tanker/overvejelser ved opbygning/afgrænsninger i measure, eventuelle faldgrupper/corner-cases osv.
![image](https://github.com/DataOgDigitalisering/dokumentation/assets/116676022/6ad82b8d-091d-45af-b133-c0cf4c1675b9)

## Measure 2
Skal dokumentere filtre og figurer (klar struktur, overvej vedligeholdelse + hvor der skal dokumenteres)
![image](https://github.com/DataOgDigitalisering/dokumentation/assets/116676022/cd1d34b2-7afc-4891-b830-338a568c3c6b)




# Exitsurvey Tidligere

Exit-undersøgelsesfanen i HR Strategisk Dashboard tager afsæt i Exitsurveyen, som automatisk udsendes til alle personer, der frivilligt fratræder. 

## Resume af tabeller

### v_DimExitSurveyRespondent

| **View** | **Baseret på** | 
| - | - |
| [chru_cube].[v_DimExitSurveyRespondent] | [DM_FL_HR].[SD_EXITSURVEY_RESPONSES] |



### v_FactExitSurvey

| **View** | **Baseret på** | 
| - | - |
| [chru_cube].[v_FactExitSurvey] | [DM_FL_HR].[SD_EXITSURVEY_RESPONSES] [DM_FL_HR].[SD_EXITSURVEY_STRUCTURE] [DM_FL_HR].[SD_EXITSURVEY_LABELS] |



### v_TallyAmbassadør

| **View** | **Baseret på** | 
| - | - |
| [chru_cube].[v_TallyAmbassadør] | - |
v_TallyAmbassadør er en hjælpetabel, som benyttes til at danne et ambassadørfilter i HR Strategisk Dashboard, som kan trækkes ned over visningerne. Tabellen indeholder to kolonner: ID og Ambassadørtype. I tabellen svarer ambassadørtypen "Ikke ambassadør" til ID=0, mens ambassadørtypen "Ambassadør" svarer til ID=1. Den enkelte respondent får tilddelt et ambassadørFilter-ID (0 eller 1) i viewet v_FactExitSurvey. 



### (v_DimOrgDrill)

| **View** | **Baseret på** | 
| - | - |
| [chru_cube].[DimOrgDrill] | [chru_cube].[v_DimOrganisation] |



## HR Strategisk dashboard
Exit-undersøgelsen indgår som en selvstændig fane/side i HR Strategisk Dashboard.


**Beregninger**


Kommer snart og tester

Tester lige lidt...



## Tabel_skabelon
**Bygger på følgende views**:
- [link til view fra denne folder](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder)

**Ekstra informationer om tabellen**:
- vigtige tanker/overvejelser ved dannelsen af tabellen
- vigtige tanker/overvejelser ved afgrænsning af data
- Hvornår/hvordan opdateres den - skal den opdateres manuelt nogle gange (f.eks. hvis der er nogle værdier som er hard-coded ind el.lign.)
- Andet

**Ekstra informationer om kolonnerne**:
- vigtige tanker/overvejelser ved dannelsen af kolonner
- vigtige tanker/overvejelser ved afgrænsning af data
- Andet
