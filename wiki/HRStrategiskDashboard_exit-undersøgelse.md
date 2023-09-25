# Introuktion
Herunder er alle figurer i fanen Exit-undersøgelse i HR Strategisk Dashboard beskrevet:

# Svarprocent of antal besvarelser
Figuren angiver svarprocent, svarværdi og ambassadørviljen fordelt på hhv. stilling og organisation.

- Figuren bygger op følgende measures og etiketter:
  - Svar-pct. viser [Exit - Svarprocent]
  - Antal svar viser [Exit - AntalSvar]
  - Ambassadørvilje viser [Exit - Ambassadørvilje]

- Følgende filtreringer er benyttet:
  - Filtrer på siden og slicer:
    - Ingen
  - Filter på figuren:
    - Center, Afdeling og svar-pct. == not blank
    - v_DimExitSurveyRespondent[Status] == Gennemført
       v_DimTidDato'[12MdrIntervallerAfsluttede] == seneste 12 afsluttede mdr.
  - Filtrer i measures:
    - Ingen
  - Angiv de **filtreringer som er blevet benyttet i de measures** som figuren bygger på.
  - Andre bemærkninger:
    - Vigtige informationer om figuren og hvad den viser/ikke viser.
    - Vigtige tanker/overvejelser ved opbygning/afgrænsninger, eventuelle corner-cases osv.
