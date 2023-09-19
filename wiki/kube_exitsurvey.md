# Introduktion til temaet
ExitSurvey (også kaldet Exit-undersøgelse) er et tema i HR Strategisk Dashboard. Nedenstående beskriver de tabeller, kolonner og measures i CHRU_HRKube som knytter sig til temaet. Under fanen "HR Strategisk Dashboard" i sidemenuen kan du læse mere om de figurer som optræder i dashboardet.

# Tabeller og kolonner
Nedenfor er tabeller, kolonner og relationer beskrevet. Der er også blevet trukket noget metadata fra CHRU_HRKube'n i produktion, dette kan ses i de vedhæftede Excel-filer:

<details><summary markdown="span">Oversigt over tabeller og kolonner</summary>
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

## v_FactExitSurvey
Tabellen bygger på viewet [*v_FactExitSurvey*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_FactExitSurvey.sql). I sit arbejde med tabellen er det vigtigt at være opmærksom på følgende:
- Selvom tabellen bliver processeret dagligt, bliver data kun indlæst én gang om måneden og går pt. kun ét år tilbage. Dette er sikret ved at benytte følgende where-clause (leverancedato er en dato som SurveyXact opgiver):
```sql
WHERE ...
    AND Leverancedato < DATEFROMPARTS(YEAR(GETDATE()),MONTH(GETDATE()),1)
    AND Leverancedato >= DATEFROMPARTS(YEAR(GETDATE())-1,MONTH(GETDATE()),1)
```
- Tabellen indeholder kun svar fra gennemførte surveys, og hvis en person ved en fejl har fået tilsendt flere surveys til samme tjenestenummer vælges det først besvarede survey ud.
- Mange af spørgsmåls- og svarteksterne er hard-coded i viewet. Man skal derfor altid tjekke viewet efter, hvis der bliver ændret i surveyets ordlyd, temaer, svarmuligheder mm.

## v_DimExitSurveyRespondent
Tabellen bygger på viewet [*v_DimExitSurveyRespondent*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_DimExitSurveyRespondent.sql). I sit arbejde med tabellen er det vigtigt at være opmærksom på følgende:
- Data i tabellen bliver kun indlæst én gang om månened. Dette bliver gjort  på samme måde som for tabellen v_FactExitSurvey.
- Tabellen indeholder alle respondente, men hvis en person ved en fejl har fået tilsendt flere surveys til samme tjenestenummer vælges det først besvarede survey ud på samme måde som i v_FactExitSurvey.
- Kolonnen "Ambassadørfilter" angiver om man er ambassadør. Man er ambassadør hvis man har svaret "enig" eller "meget enig" til at man vil anbefale sin afdeling som arbejdsplads til en ven eller kollega. Dette bygger på noget teori som viser at netop dette spørgsmål er sigende for hvor tilfreds man har været med sin arbejdsplads.

## v_TallyAmbassadør
Tabellen bygger på viewet [*v_TallyAmbassadør*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_TallyAmbassad%C3%B8r.sql). I sit arbejde med tabellen er det vigtigt at være opmærksom på følgende:
**Ekstra informationer om tabellen**:
- Dette er en simpel Tally-tabel. Den er lavet for at kunne lave en slicer hvor både "ambassadør" og "ikke ambassadør" vises, også selvom man har filtreret ned på en gruppe som kun består af fx ambassadører.

# Measures
Her er de measures som knytter sig til temaet Exit-undersøgelse beskrevet. Der er blevet trukket noget metadata fra CHRU_HRKube'n i produktion, dette kan ses i Excel-filen nedenfor. Herudover er enkelt measures beskrevet mere detaljeret.

<details><summary markdown="span">Oversigt over measures</summary>
<b>Measures</b>
<center>
<iframe width="100%" height="800" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>  

## Exit - Anonymitetsgrænse
- Inputværdier/Filtrer:
  - Ingen
- Returværdier:
  - Anonymitetsgrænse
- Uddybende bemærkninger:
  - Denne værdi følger den som også gælder for trivselsdata og onboarding. Den bruges også i fanen "onboarding".
