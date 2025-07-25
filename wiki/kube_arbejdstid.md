# Arbejdstid
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Arbejdstid" beskrevet.

## Ændring i normtid over seneste afsluttede 12 mdr
- Antallet af personer der går hhv. op eller ned i normtid beregnes i DAX gennem 3 measures: [AntalOpITidSidste12Mdr], [AntalNedITidSidste12Mdr] og [AntalSammeTidSidste12Mdr].
- Beregningen baseres på de medarbejdere, som var ansat i både starten og slutningen af seneste afsluttede 12 mdr., mens medarbejdere, som er fratrådt eller tiltrådt i perioden ikke medtælles.
- Slutdatoen for perioden er sat til 'v_DimTidDato'[Filterdatoer] = "Sidste dag i sidste måned".

## 6 udvalgte faggrupper i fokus
I figuren "Udvikling i gennemsnitlig ugentlig normtid for udvalgte fagstillingsgrupper" er der lagt et filter på fagstillingsgrupper ind i PowerBI-filen, så der kun vises 6 faggrupper (Bioanalytikere, Jordemødre, Lægepersonale, Radiografer, SOSU’er og Sygeplejer-personale). De seks faggrupper er udvalgt, fordi der er et politisk fokus på netop disse faggrupper, bl.a. i regionens Fastholdelses- og rekrutteringsudvalg. De 6 faggrupper går også igen andre steder i dashboardet.

## Tallytabel for Arbejdstidsintervaller
Fordelingen af medarbejderne på gennemsnitlg ugentlig normtid sker gennem en tallytabel [v_TallyArbejdstidsintervaller], hvori intervallerne er defineret. Tallytabellen kan ændres ved at ændre i view-koden.

# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="1200" height="300" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Arbejdstid_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="1200" height="300" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Arbejdstid_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

<b>Measures</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Arbejdstid_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
