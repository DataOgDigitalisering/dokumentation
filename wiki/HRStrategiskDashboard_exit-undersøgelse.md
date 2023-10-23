# Exit-undersøgelse - HR Strategisk Dashboard
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Exit-undersøgelse" beskrevet.

# Anonymisering og indlæsning af data
- Man skal være opmærksom på at nye besvarelser på exit-survey kun indlæses i kuben én gang om måneden. Dette er beskrevet mere i de views som exit-undersøgelsen benytter. Denne beslutning med blev truffet for sikre en højere grad af anonymisering.
- Data vises ikke ved grupperinger på mindre end 5. Dog vises svarprocent og antal besvarelser også selvom man ser på mindre end 5 personer.

# Opbygning af views
- De to views [*v_DimExitSurveyRespondent*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_DimExitSurveyRespondent.sql) og [*v_FactExitSurvey*](https://github.com/DataOgDigitalisering/versionsstyringViews/blob/Produktion/viewFolder/v_FactExitSurvey.sql) som knytter sig til Exit-undersøgelsen indeholder en del tekst som er er hard-coded. Hvis spørgsmålenes ordlyd eller svarene ændres er det derfor vigtigt at opdatere de to views.
- Nogle personer har ved en fejl fået udsendt mere end ét survey på samme tjenestenummer. Disse ekstra surveys bliver filtreret fra i de to views.

# Ambassadørfilter og ambassadørvilje
Tanken bag ambassadørfilteret udspringer af Net Promoter Score, som er et mål for hvorvidt en ansat eller kunde er ambassadør for en virksomhed. Ved at filtrere på ambassadører/ikke ambassadører kan vi få et indblik i pull/push factors.
