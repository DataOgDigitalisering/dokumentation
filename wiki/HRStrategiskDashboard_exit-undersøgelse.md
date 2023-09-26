# Introuktion
Herunder er alle figurer i fanen Exit-undersøgelse i HR Strategisk Dashboard beskrevet:

# Svarprocent of antal besvarelser
Figuren angiver svarprocent, svarværdi og ambassadørviljen fordelt på hhv. stilling og organisation.

**Figuren bygger op følgende measures og etiketter**:
- Svar-pct. benytter measuret [Exit - Svarprocent].
- Antal svar benytter measuret [Exit - AntalSvar].
- Ambassadørvilje benytter measuret [Exit - Ambassadørvilje].

**Følgende filtreringer er benyttet**:
- Filtrer på siden og filtervalg:
  - Ingen
- Filtrer på figuren:
  - v_DimOrganisation[Center], v_DimOrganisation[Afdeling] og svar-pct. == not blank
  - v_DimExitSurveyRespondent[Status] == Gennemført
  - v_DimTidDato'[12MdrIntervallerAfsluttede] == seneste 12 afsluttede mdr.
- Filtrer i measures:
  - [Exit - Svarprocent] og [Exit - AntalSvar] indeholder ingen filtreringer. Men fordi filteret v_DimExitSurveyRespondent[Status] == Gennemført virker på figuren, medregner vi ikke delvist besvarede under gennemførte surveys.
  - [Exit - Ambassadørvilje] deffinerer en periode via.
```
VAR __StartPeriode =
    MIN ( v_DimTidDato[Dato] )

VAR __SlutPeriode =
    EDATE ( __StartPeriode , 12 ) - 1 
```
og filtrer med where-calusen
```
v_DimExitSurveyRespondent[Leverancedato] >= __StartPeriode,
v_DimExitSurveyRespondent[Leverancedato] <= __SlutPeriode,
```
Og inkluderer kun 

- Andre bemærkninger:
  - Vigtige informationer om hvad figuren og hvad den viser/ikke viser.
  - Vigtige tanker/overvejelser ved opbygning/afgrænsninger, eventuelle corner-cases osv.
