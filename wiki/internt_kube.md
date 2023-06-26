# Introduktion - UNDER UDVIKLING
Denne side beskriver de ting som man skal være opmærksom på når man bygger og arbejder med kuber.

# Arbejd med kuber
navngivning + dokumentation + flyt arbejde mellem kuber

# Brugerstyring og roller
I *Tabular Editor* kan man 
både tab editor + ssms
Jeg mener at folk kan tilgå measrues gennem DAX-Studio, så pas på med hvad du skriver...

# Tabeller og relationer
navn, definition, parititioner, kolonner, navn, type, format, sort by  navngivning, secutirycorssfiltering, 

# Measures
navn, mappe, Opbygning, __foran variabel?, format, type, 
Rækkefølgen på fanerne er også vigtig. Alle temaer og deres tilhørende undersider kommer først. Herefter kommer alle sider med filtervalg, og til sidst kommer alle sider med tooltips. Dette kan f.eks. ses i *HR Strategisk Dashboard*.


#Gamle ting
### Tabeller
- Navngives som fx v_DimAnsættelse
- Skabelon: [tabeltype]+[\_]+[Formål]+[BeskrivendeNavn]
- **Views** indledes med __v\___ 
  - Alt *efterfølgende* skrives i camelCase (**S**tort**B**egyndelsesbogstav)
  - **Formål**: Dim, Fact, Security, Info, Slicer, Tally.
  - **Beskrivende navn** er entydig(e) og letforståelig(e) *substantiv(er)*. (Gerne noget der minder om rådatatabellens oprindelige navn hvis viewet er baseret på en sådan). Sammensatte ord skrives i camelCase

- **Tabeller** navngives som views. [Formål]+[**B**eskrivende**N**avn]. Fx DimLønart
  - __v\___ udelades

- **Kolonnenavne** er entydige og letforståelige *substantiver*
  - camelCase
  - Disse felter udfyldes i Tabular Editor, hvis ikke de er pre-udfyldt:
    - Data Type
    - Description
    - Key


### Calculated columns
  - Undgå så vidt muligt datatransformation i Tabular Editor. Det giver bedre overblik at have samlet i SQL.
    - (Flyt evt nedenstående til views og brug en mere robust metode til anonymisering:)
      - v_DimAnsættelse[TjnrAnonymiseret]
      - v_DimPerson[NavnAnonymiseret]   


### Stored procedures
  - Navngives kort og præcist beskrivende fx 'DanskeHelligdage'
  - Brug så vidt muligt verber til at beskrive procedurens *funktion*
  - camelCase

- æ, ø, å tilladt


### Measures
- Navngives fx [Fravær - vægtede fuldtidsfraværsdage]. 
- Skabelon: [tema - beskrivende og letforståelig tekst]
  - (ikke nødvendigvis camelCase)
- Measures grupperes i temaspecifikke mapper
  - Enkelte basis-measures placeres i mappen _Diverse_, hvis de bruges på tværs af temaer. Fx [Antal fuldtidsansatte] og [FilterSlicer]
- æ ø å tilladt
- Ikke alle measures er navngivet efter denne konvention. Ved tvivl se mappen _Sygefravær_
- Disse felter udfyldes i Tabular Editor, hvis ikke de er pre-udfyldt:
  - Description
<br>

