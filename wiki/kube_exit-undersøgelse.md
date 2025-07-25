# Exit-undersøgelse - HR Strategisk Dashboard
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Exit-undersøgelse" beskrevet.

## Anonymisering og indlæsning af data
- Man skal være opmærksom på at nye besvarelser på Exit-survey kun indlæses i kuben én gang om måneden. Dette er beskrevet mere i de views som Exit-undersøgelsen benytter. Denne beslutning blev truffet for sikre en højere grad af anonymisering.
- Den aggregerede data vises ikke ved grupperinger på mindre end 5. Dog vises svarprocent og antal besvarelser selvom man ser på mindre end 5 personer.

## Opbygning af views
- De to views [*v_DimExitSurveyRespondent*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_DimExitSurveyRespondent.sql) og [*v_FactExitSurvey*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_FactExitSurvey.sql) som knytter sig til Exit-undersøgelsen indeholder en del tekst som er er hard-coded. Hvis spørgsmålenes ordlyd eller svarmulighederne ændres, er det derfor vigtigt at opdatere de to views.

## Fejl i data
- Nogle personer får ved en fejl udsendt mere end ét survey på samme tjenestenummer. Disse ekstra surveys bliver filtreret fra i de to views.
- I en periode på ca. 40 dage i efteråret 2024 modtog fratrådte medarbejdere ikke surveys, da der var en fejl i Rambølls system, som blokerede for udsendelsen af surveys til oprettede respondenter gennem brugen af en API. De fejloprettede respondenter frasorteres i views (gennem en wehere clause i DimExitSurveyRespondent digitald != 3) og er efterfølgende oprettet på ny og har fået tilsendt et survey.

## Ambassadørfilter og ambassadørvilje
I udarbejdelsen af dashboardet er det i fællesskab med Lededelse og Organisation besluttet, at definere en ambassadør som en tidligere medarbejder, der svarer, at de i høj grad eller i meget høj grad vil anbefale regionen som arbejdsplads til en ven eller kollega. Tanken bag ambassadørfilteret udspringer af Net Promoter Score, som er et mål for hvorvidt en ansat eller kunde er ambassadør for en virksomhed. Ved at filtrere på ambassadører/ikke ambassadører kan vi få et indblik i pull/push factors.

# Tabeller og kolonner
Nedenfor er tabeller, kolonner og relationer beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>

<b>Relationer</b>
<center>
<iframe width="1200" height="200" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Relationer&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet Exit-undersøgelse beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

<b>Measures</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Exit_unders%C3%B8gelse_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
