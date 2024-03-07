# Der arbejdes på at få denne side klar!

<center><img src="Images/sideUdarbejdes.png" height="95%" width="95%" style="vertical-align:middle"/></center>


# Forbrug
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Forbrug" beskrevet.

## Der arbejdes på dette afsnit
TODO


# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="100%" height="500" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

Flere measures er baseret på measuret *Løngennemsnit*. Løn gennemsnittet er gennemsnittet af alle de udbetalte lønningerne på hvert tjenestenummer. Der anvendes ikke gennemsnit af gennemsnit. <br>
Skulle measuret skrives i SQL kan det gøres sådan her.

``` sql
SELECT AVG(LØN) FROM 
    (
    SELECT SUM(BELØB) AS LØN
    FROM DM_FL_HR.FactForbrug
    GROUP BY 
    TJNR, PRAE_PERIODE
    ) as Månedslønninger
```

I Dashboardet er det muligt at skifte mellem tre beregningsmetoder. Skiftet mellem beregningsmetoder er indlejret i de forskellige measures. 
1. Lønforbrug inkl. ferie (Her anvendes kolonnen **BELØB**)
2. Lønbrug ekskl. ferie (Her anvendes kolonnen **BELØB**, men grundkategorien **Ferie/løn** er sorteret fra)
3. Omregnet til fuldtid (Her anvendes kolonnen **BELØB_FULDTID**, men grundkategorierne **Ferie/løn** og **Særydelser** er sorteret fra. Beløbene omregnes ved at dividere Beløb kolonnen med medarbjederens beskæftigelsesdecimal)
<b>Measures</b>
<center>
<iframe width="100%" height="800" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Forbrug_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Ekspert Dashboard
For mere information om ekspertdashboardet. Se [Github repository](https://github.com/DataOgDigitalisering/ekspertdashboard)

Programmet fungere ved at resultatet af de fire queries personoversigt, tilloversigt, autorisationer og specialer eksportes til CSV filer. 
Excelfilen ekspertdashboard anvendes som skabelon og er forbundet til de CSV filer. Programmet henter generere nye CSV og data i Excelfilen opdateres. <br><br>
Derefter vedhæftes Excelfilen og Word Brugervejledningen i en mail, som sendes til de email adresser der findes i filen modtagere.txt <br><br>
CSV, Word og Excelfilen findes i denne mappe 

``` bat
L:\LovbeskyttetMapper\DataProjekterOgAdHoc\Projekt Løn\Løn Dashboard\Ekspert dashboard\til udsendelse
```

