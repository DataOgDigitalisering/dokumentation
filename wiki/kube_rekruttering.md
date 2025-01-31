# Rekruttering
Rekrutteringstemaet baserer sig på data fra HR Manager. Regionen har imidlertid fået et nyt rekrutteringssystem Talent Recruiter og der kommer derfor (fra oktober 2024) ikke længere nyt data i HR Manager. 

Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Rekruttering" beskrevet med afsæt i de tabeller, der baserer sig på HR Manager.

## Rekrutteringstemaet er ikke koblet til resten af CHRU_Kube
Rekrutteringstemaet baserer sig på Region Hovedstadens rekrutteringssystem HR Manager. Eftersom det desværre ikke er muligt at koble oplysningerne for personer, der endnu ikke er ansat til et Tjnr, er det kun muligt at benytte de personoplysninger, som findes i Hr manager. I praksis betyder det følgende:
1) I modsætning til de øvrige temaer i CHRU_Kube, er Rekrutteringstemaet ikke koblet til Lønsystemets Stillings- og Organisationshierarki. I stedet anvendes de oplysninger om Viksomhed, Fagstillingsgruppe og Stillingsgruppe, som findes i HR Manager.
2) Åbner man HR strategisk Dashboard., vil man se, at filtrene under temaet "Rekruttering" er baseret på rekrutteringssystemets organisations- og stillings-hierarkier, som kan afvige fra de tilsvarende hierarkier i lønsystemet. DeDet er f.eks. ikke muligt at filtrere på et lavere niveau end virksomhedsniveau.
3) Alle oplysninger slettes efter 6 mdr., eftersom vi ikke opbevarer oplysninger om personer, der endnu ikke er ansat (f.eks. ansøgere).

## Median eller gennemsnit
Som nøgletal anvendes ofte medianen af ansøgere pr. stillingsopslag i stedet for det gennemsnitlige antal ansøgere pr. stillingsopslag, eftersom gennemsnittet kan blive påvirket af, at der kommer unormalt mange ansøgere til enkelte stillingsopslag.

# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="1200" height="300" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Rekruttering_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Sygefrav%C3%A6r_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

<b>Measures</b>
<center>
<iframe width="1200" height="300" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Rekruttering_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
