# Introduktion til temaet
kort lille tekst

# Tabeller og kolonner
Her er de tabeller som knytter sig til temaet Exit-undersøgelse beskrevet i mere detalje

## Oversigt over tabeller og kolonner

<details><summary markdown="span">Oversigt over kuben</summary>
 
Tabeller
<center>
<iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
Kolonner
<center>
<iframe width="100%" height="500" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>

Relationer
<center>
<iframe width="100%" height="150" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Relationer&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>  
<br>

## Beskrivelse af hver tabel
Nedenfor er alle tabeller som knytter sig til temaet Exitsurvey beskrevet.
## Tabel 1
- Hvad den bygger på af views + råtabeller,  Dette skal suppleres af SQL og SAS-kode som skal være i sit eget repository på GitHub – gerne linket direkte til det her.
 Vigtige informationer om given tabel. Hvad er dens funktion, hvordan bruges den, vigtige tanker/overvejelser ved dannelsen af kolonner/afgrænsning af data. Hvornår opdateres den?

- lav oversigt i excel over tabel + kolonner
- Lav oversigt over relationer fra denne tabel til andre + beskriv dem kort.

## Tabel 2

Beskrivelse af selve tabellen (ikke mere end 100 tegn).
Liste over alle kolonner (minder om SD’s dokumentation):
Key, Kolonnenavn, Datatype, Len, Null’s, Beskrivelse af hvad kolonnen viser (ikke mere end 100 tegn) med eksempel på værdi
Beskrivelse skal ind som ”description” i TabularEditor – dvs. listen kan stort set autogenereres…


# Measures
Her er de measures som knytter sig til temaet Exit-undersøgelse beskrevet i mere detalje.

## Oversigt over measures
<details><summary markdown="span">Oversigt over measures</summary>
 
Measures
<center>
<iframe width="100%" height="800" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>  

## Measure 1






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



## HR Strategisk dahboard
Exit-undersøgelsen indgår som en selvstændig fane/side i HR Strategisk Dashboard.


**Beregninger**


Kommer snart og tester

Tester lige lidt...
