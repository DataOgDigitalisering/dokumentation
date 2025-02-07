# Forbrug
Forbrugstabellerne indgår i løntemaet i HR Strategisk dashboard og i Ekspertdashboardet. Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Forbrug" beskrevet.

# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="1200" height="200" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="1200" height="200" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

Flere measures er baseret på measuret *Løngennemsnit*. Løngennemsnittet er gennemsnittet af alle de udbetalte lønninger på hvert tjenestenummer. Der anvendes ikke gennemsnit af gennemsnit. <br>
Skulle measuret skrives i SQL kan det gøres sådan her:

``` sql
SELECT AVG(LØN) FROM 
    (
    SELECT SUM(BELØB) AS LØN
    FROM DM_FL_HR.FactForbrug
    GROUP BY 
    TJNR, PRAE_PERIODE
    ) as Månedslønninger
```

I Dashboardet er det muligt at skifte mellem tre beregningsmetoder. Skiftet mellem beregningsmetoder er indlejret i de forskellige measures. De tre beregningsmetoder er:
1. Lønforbrug inkl. ferie (Her anvendes kolonnen **BELØB**)
2. Lønbrug ekskl. ferie (Her anvendes kolonnen **BELØB**, men grundkategorien **Ferie/løn** er sorteret fra)
3. Omregnet til fuldtid (Her anvendes kolonnen **BELØB_FULDTID**, men grundkategorierne **Ferie/løn** og **Særydelser** er sorteret fra. Beløbene omregnes ved at dividere Beløb kolonnen med medarbjederens beskæftigelsesdecimal)
<b>Measures</b>
<center>
<iframe width="1200" height="500" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Ekspertdashboard
For mere information om ekspertdashboardet, se [Github repository](https://github.com/DataOgDigitalisering/ekspertdashboard)

Programmet fungerer ved, at resultatet af flere SQL queries eksportes til CSV filer. 
Excelfilen "Ekspertdashboard" anvendes som skabelon og er forbundet til disse CSV-filer. Programmet henter/genererer nye CSV og data i Excelfilen opdateres. <br><br>
Derefter kopieres Excelfilen og placeres på en delt L-drevs placering <br><br>
CSV-filerne, Excelfilen og en vejledning til brugerne findes i denne mappe:

``` bat
L:\LovbeskyttetMapper\DataProjekterOgAdHoc\Projekt Løn\Løn Dashboard\Ekspert dashboard\til udsendelse
```

