# Overblik over views, tabeller og kuben
Her er de scripts og metoder som vi benytter til at få overblik over tabeller, views og measures beskrevet. De bruges til at give et overblik over hvad der ligger i udvikling og produktion fx ifm. oprydning.

## Overblik over kuben
Vi har et program som genererer en liste over alle de measures og kolonner som bliver benyttet i et givent dashboard. Det viser også om et measure bliver brugt i andre measures, og om kolonner fx. indgår i relationer eller i RLS. Programmet ligger i følgende repository [pbixAnalyzer](https://github.com/DataOgDigitalisering/pbixAnalyzer).

## Overblik over views og tabeller
Vi har flere scripts som kan benyttes til at give et overblik over de tabeller og views som ligger i udvikling og produktion.
- Vi har et program som kan bruges til at gemme samtlige views i GitHub. Programmet gemmer alle views med skemanavnet [chru_cube] fra enten udvikling eller produktion. Dette kan bruges til versionsstyring eller som backup inden man laver større ændringer. Programmet ligger i følgende repository [versionsstyringViews](https://github.com/DataOgDigitalisering/versionsstyringViews).
- Vi har flere programmer som kan benyttes til at sammenligne tabeller og views i produktion og udvikling. Programmerne er skrevet i SQL og kan ses her [standardscripts_tabeller_views](https://github.com/DataOgDigitalisering/standardscripts_tabeller_views).
