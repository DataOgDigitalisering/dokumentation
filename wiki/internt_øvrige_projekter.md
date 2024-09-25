# Øvrige projekter:
- [Puzzel](#puzzel)
- [Barselsberegner](#barselsberegner)
- [HRS dashboards](#hrs-dashboards)
- [Tjenestetid](#tjenestetid)
- [48 timer](#48-timer)
- [Vagtskemaer](#vagtskemaer)
- [Setup omkring faste leverancer](#setup-omkring-faste-leverancer)
- [Statsborgerskab ✓](#statsborgerskab-✓)
- [Automatisering af brugeradministration](#automatisering-af-brugeradministration)
- [Nye Ledere](#nye-Ledere)
- [Cheflønsmonitorering](#cheflønsmonitorering)
- [Fejl registrering af LED koderne i HR-service](#fejl-registrering-af-LED-koderne-i-HR-service)
- [Lederkode](#lederkode)
- [P sag dokument udtræk](#p-sag-dokument-udtræk)

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
| CPR                 | Medarbejder CPR  |
| Mappenavn           | Mappen i personalesagen [^1]  |
| Dokumenttype        | Skabelon ID FK  |
| Dokumenttitel       | Titel på dokumentet  |
| Filtype             | Filendelse for dokumentet  |
| Afsenderbrugernavn  | CBAS brugernavn for uploader typisk leder eller HR-konsulent |
| Afsendernavn        | Afsenderens navn | 
| Oprettelsestidspunkt| Hvornår blev dokumentet lagt på sagen [^2]|
| Laast               | Kan dokumentet redigeres (kladde tilstand)  |
| Slettet             | Hvornår blev dokumentet slettet. Null hvis dokumentet ikke er slettet  |


De mest væsentlige kolonner i `[LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTTYPER_SKABELONER]`

| Kolonne navn        | Forklaring    |
| -------------       | ------------- |
| ID                  | Skabelon id PK  |
| Navn                | Skabelonens navn  |
| Type                | Skabelonens type. Enten dokumentType eller dokumentSkabelon [^3]  |
| Status              | Angiver om skabelonen er aktiv eller slettet  |
| Afsenderbrugernavn  | CBAS brugernavn for uploader  |
| Tilgaengelig        | Kan skabelonen anvendes[^4]  |

Eksempel join 

``` sql
SELECT *
FROM [LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTER] dokumenter
-- ikke alle dokumenter har en tilhørende skabelon eller dokumenttype
LEFT JOIN [LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTTYPER_SKABELONER] skabeloner ON skabeloner.ID = dokumenter.dokumenttype
```

Dokumenttitlen kan indeholde flettefelter. I flettefleterne vil der typisk være indsat institution og afdeling for den medarbejder som dokumentet vedrører. For medarbejdere med flere ansættelser skal fletteværdien vælges inden dokumentet uploades. 

Personale sagen er på person niveau, så CPR anvendes som nøgle til øvrige tabeller.

``` sql
SELECT 
dokumenter.CPR,
person.TJNR --Samtidige ansættelser vil returene begge TJNR

FROM [LON_HR].[SD_SYSTEM_INFO].[V_SD_DOKUMENTER] dokumenter

LEFT JOIN [LON_HR].[SD].[SD_Person] person ON Person.CPR = dokumenter.CPR 
    AND CONVERT(date,dokumenter.Oprettelsestidspunkt) BETWEEN person.[Start] AND person.Slut 
    AND person.stat in (0,1,3)
```

[^1]: Mappe 9 også kaldet ledermappen indeholder TJNR i navnet

[^2]: Nogle gange bliver samme dokument uploaded flere gange inden for kort tid

[^3]: DokumentSkabelon er en skabelon i tradiotionel forstand. Det er et dokument, som man kan få genereret. Der er en masse forudfyldt tekst og eksempelvis virksomhedsnavn og adresse bliver flettet ind. <br>DokumentType anvendes til at kategorisere et dokument, som ikke er genereret gennem Personale-web. Det kan eksempelvis være en medarbejder som har indsendt en straffeattest eller et bevis for et bestået kursus. 

[^4]: Kolonnen har værdien "frigivet" eller "ej frigivet". I personale-web vises der en rød eller grøn markering, ud fra skabelonen. Det angiver om skabelonen kan anvendes. Kun synligt for medarbejdere med udvidet rettigheder. 