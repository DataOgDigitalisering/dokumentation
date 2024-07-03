# Øvrige projekter:
- [Puzzel](#Puzzel)
- [Barselsberegner](#Barselsberegner)
- [HRS dashboards](#HRS-dashboards)
- [Tjenestetid](#Tjenestetid)
- [48 timer](#48-timer)
- [Vagtskemaer](#Vagtskemaer)
- [Setup omkring faste leverancer](#Setup-omkring-faste-leverancer)
- [Statsborgerskab ✓](#Statsborgerskab-✓)
- [Automatisering af brugeradministration](#Automatisering-af-brugeradministration)
- [Nye Ledere](#Nye-Ledere)
- [Cheflønsmonitorering](#Cheflønsmonitorering)
- [Fejl registrering af LED koderne i HR-service](#Fejl-registrering-af-LED-koderne-i-HR-service)
- [Lederkode](#Lederkode)
- [P sag dokument udtræk](#P-sag-dokument-udtræk)

## Puzzel
## Barselsberegner
## HRS dashboards
## Tjenestetid
## 48 timer
## Vagtskemaer
## Setup omkring faste leverancer
## Statsborgerskab ✓
## Automatisering af brugeradministration
## Nye Ledere
## Cheflønsmonitorering
## Fejl registrering af LED koderne i HR-service
## Lederkode
## P sag dokument udtræk
Til udtræk af dokumeter på P sagen, anvendes to tabeller fra P01.
Data leveres en gang månedligt d. 10 i måneden. 

`[LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTER] dokumenter`

`[LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTTYPER_SKABELONER] skabeloner`

De mest væsentlige kolonner i `[LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTER]`


| Kolonne navn        | Forklaring    |
| -------------       | ------------- |
| CPR                 | Mdarbjeder CPR  |
| Mappenavn           | Mappen i personalesagen  |
| Dokumenttype        | Skabelon ID FK  |
| Dokumenttitel       | Titel på dokumentet  |
| Filtype             | Filendelse for dokumentet  |
| Afsenderbrugernavn  | CBAS brugernavn for uploader typisk leder eller HR-konsulent |
| Afsendernavn        | Afsenderens navn | 
| Oprettelsestidspunkt| Hvornår blev dokumentet lagt på sagen  |
| Laast               | Kan dokumentet redigeres (kladde tilstand)  |
| Slettet             | Hvornår blev dokumentet slettet. Null hvis dokumentet ikke er slettet  |


De mest væsentlige kolonner i `[LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTTYPER_SKABELONER]`

| Kolonne navn        | Forklaring    |
| -------------       | ------------- |
| ID                  | Skabelon id PK  |
| Navn                | Skabelonens navn  |
| Type                | Skabelonens type. Eneste mulighed er dokument  |
| Status              | Angiver om skabelonen er aktiv eller slettet  |
| Afsenderbrugernavn  | CBAS brugernavn for uploader  |
| Tilgaengelig        | Er dokumenter ud fra skabelonen synlige for medarbjederen  |

Eksempel join 
``` sql
SELECT *
FROM [LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTER] dokumenter

-- ikke alle dokumenter har en tilhørende skabelon
LEFT JOIN [LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTTYPER_SKABELONER] skabeloner ON skabeloner.ID = dokumenter.dokumenttype
```
