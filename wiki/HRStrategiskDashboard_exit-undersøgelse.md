# Introuktion
Herunder er alle figurer i fanen Exit-undersøgelse i HR Strategisk Dashboard beskrevet:

# Svarprocent of antal besvarelser
Figuren angiver svarprocent, svarværdi og ambassadørviljen fordelt på hhv. stilling og organisation.

**Figuren bygger op følgende measures og etiketter**:
- Svar-pct. benytter measuret [Exit - Svarprocent].
- Antal svar benytter measuret [Exit - AntalSvar].
- Ambassadørvilje benytter measuret [Exit - Ambassadørvilje].

**Følgende filtreringer er benyttet**:
- Filtrer på siden og default filtervalg:
  - Ingen
- Filtrer på figuren:
  - ```v_DimOrganisation[Center], v_DimOrganisation[Afdeling] og [Exit - Svarprocent] == not blank```
  - ```v_DimExitSurveyRespondent[Status] == Gennemført``` dvs. vi kategorsirer ikke delvist besvarede surveys som besvarede.
  - ```v_DimTidDato'[12MdrIntervallerAfsluttede] == seneste 12 afsluttede mdr.```
- Filtrer i measures:
  - [Exit - Svarprocent] og [Exit - AntalSvar] indeholder ingen yderligere filtreringer.
  - [Exit - Ambassadørvilje] inkludrer kun gennemførte surveys hvor ```v_DimExitSurveyRespondent[Leverancedato]``` ligger indenfor en 12 måneders periode:
     ```
    VAR __StartPeriode = MIN ( v_DimTidDato[Dato] )
    VAR __SlutPeriode = EDATE ( __StartPeriode , 12 ) - 1
    ```
