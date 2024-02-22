# Trivsel
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Trivsel" beskrevet.

## Obligatoriske og valgfri målinger
Trivselsdata opdateres i forbindelse med gennemførelsen af de årlige regionale trivselsmålinger, som gennemføres obligatorisk i 1. og 3. kvartal og valgfrit i 2. og 4. kvartal. HR Strategisk dashboard inkluderer udelukkende besvarelser på de tre fællesregionale spørgsmål, selvom der også stilles lokale spørgsmål i trivselsmålingerne.

## SD og APOS
I HR Strategisk Dashboard kan trivselsdata både vises ud fra SD- og APOS-hierarkierne. Til hvert spørgsmålsvar knyttes ogs ansættelsesID ud fra tjenestenummer og svardatoen for målingen, hvilket gør det muligt at opgøre besvarlserne ud fra SD-hierarkiet.

## Forskelle mellem det man ser som bruger i Kursusportalen og i HR Strategisk Dashboard
Aggregerings- og anonymiseringsprincipperne i HR Strategisk Dashboard er ikke identiske med principperne i Kursusportalen. Det medfører, at der i visse tilfælde – særligt på lavere enhedsniveauer – kan opstå en forskel i resultaterne i hhv. Kursusportalen og HR Strategisk Dashboard. 
- Dashboardet vil altid inkludere alle medarbejdere i den viste enhed samt alle medarbejdere i eventuelle underliggende enheder. Hvis der er mindre end fem respondenter på det valgte niveau, vil resultatet dog være anonymiseret.
- I Kursusportalen vil der derimod ske en anonymisering, som betyder at, hvis der er mindre end fem respondenter i en enhed, vil der ikke kunne dannes en rapport for enheden, og besvarelserne vil heller ikke være medtaget på overliggende niveau. Dette kan i praksis betyde, at der kan være besvarelser, der ikke indgår i det samlede resultat, hvilket også kan være problematisk, hvis de pågældendes besvarelser dermed ekskluderes.
Der kan derfor opstå diskrepans i viste gennemsnit og antal mellem de to opgørelsesmetoder.


# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="100%" height="400" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Trivsel_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="100%" height="500" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Trivsel_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

<b>Measures</b>
<center>
<iframe width="100%" height="800" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01de42f3-df69-45a9-ba70-a4e8ffee9f9a}&action=embedview&wdAllowInteractivity=False&Item=Trivsel_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>






## Svarskalaer

Overblik over de forskellige svarskaler vi benytter i forskellige spørgeskemaundersøgelser

| Emne | kategori 5 | kategori 4 | kategori 3 | kategori 2 | kategori 1 |
| -- | -- | -- | -- | -- | -- |
| Standardskema for kursusevalueringer i CHRU | Meget enig | Enig | Hverken/eller | Uenig | Meget uenig |
| Trivsel | I meget høj grad (5) | I høj grad (4) | I nogen grad (3) | I ringe grad (2) | Slet ikke (1) |
| APV | I meget høj grad (5) | I høj grad (4) | I nogen grad (3) | I ringe grad (2) | Slet ikke (1) |
| Exit-undersøgelse | I meget høj grad | I høj grad | I nogen grad | I lav grad | I meget lav grad |
| Onboarding-undersøgelse | I meget høj grad (5) | I høj grad (4) | I nogen grad (3) | I ringe grad (2) | Slet ikke (1) |
| Likert-skalaen | Meget enig | Enig | Hverken/eller | Uenig | Meget uenig |
