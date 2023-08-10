# Introduktion
I både udvikling og produktion refererer vores tabeller i kuben til views. Vores views er altså bindeled mellem kuber og tabeller. Ofte laver vi også datatransformationer og beregninger i vores views, og de spiller derfor en central rolle i vores arbejde. Afsnittene nedenfor beskriver vores arbejdsproces med views, samt nogle af de konventioner vi benytter ved navngivning af kolonner mm.

# Arbejde med views
Hvis man vil oprette nye views, eller lave ændringer på eksisterende views, skal det som udgangspunkt altid ske i vores udviklingsmiljø og under skemanavnet *[test]*. Når viewet er testet og færdigt, kan man oprette det under skemanavnet *[chru_cube]*. Alle views som kuben bygger på skal have dette skemanavn. Alle views med skemanavnet *[chru_cube]* bliver versionsstyret gennem GitHub. Dette sikrer et stabilt miljø, og gør det lettere at flytte ændringer fra udvikling til produktion. Du kan læse mere om dette under siden [*Versionsstyring - Guide*](https://dataogdigitalisering.github.io/dokumentation/internt_versionsstyring).

# Navngivning og konventioner
Vores views navngives meget på samme måde som tabellerne i kuben:

- **Views** navngives på formen [skemanavn].[tabeltype]+[\_]+[Formål]+[BeskrivendeNavn] som fx *v_DimAnsættelse*, hvor
  - *Skemnavn* skal være *[chru_cube]*, hvis det er et view som bruges i *CHRU_HRKube* på udvikling eller produktion. Ellers kan man også benytte skemanavnet *[test]*.
  - *Tabeltype* angiver at det er et view og indledes med __v\___.
  - *Formål* angiver viewets funktion i kuben og kan være *Dim, Fact, Security, Info, Slicer,* eller *Tally*.
  - *Beskrivende navn* er entydig(e) og letforståelig(e) *substantiv(er)*. Sammensatte ord skrives i camelCase (**S**tort**B**egyndelsesbogstav).
- **Kolonnenavne** skal være entydige og letforståelige *substantiver* og navngives på følgende måde:
  - Der benyttes camelCase
  - Den primære nøgle i dimensionstabeller navngives *ID*, den fremmednøgle navngives *[Beskrivende navn på dimensionstabel] + [ID]*. Dette kan fx ses i viewet *v_DimExitSurveyRespondent* som har en primærnøgle  *'v_DimExitSurveyRespondent'[ID]* og en relation til *'v_FactExitSurvey'[ExitSurveyRespondentID]*. Det er vigtigt at huske at navngive disse kolonner korrekt, ellers kan vores kuber og datamodeller hurtigt blive uoverskuelig, og det kan være svært at få overblik over relationer.
