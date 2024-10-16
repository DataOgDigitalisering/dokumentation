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
- [Kursusportalen](#kursusportalen)

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

## Kursusportalen

Kursusportalen er regionens kursusadministrationssystem (LMS), Prooffice, Plan2Learn er leverandør  af systemet. Vi har i samarbejde med dem fået udviklet en datapakke, som skal anvendes i en Power-BI løsning, der skaber overblik over regionens kursusaktiviteter og evalueringsresultater fra kurserne.

Kursusportal-projektet har eget Git-repository: [Link til repository](https://github.com/DataOgDigitalisering/Kursusportal-dashboard)

[Dokumentation lavet af Prooffice findes i Github](https://github.com/DataOgDigitalisering/Kursusportal-dashboard/blob/main/Dokumentation_Datapakke_Kursusportalen.pdf)

### Datastruktur

Kursusaktiviteterne er hierarkisk opbygget i 4 niveauer:
1. **Education (Uddannelse):** En uddannelse består af et eller flere kurser. Ikke alle kurser tilhører en uddannelse. Et kursus kan være del af mere end en uddannelse. Uddannelser anvendes kun i begrænset omfang.
2. **Course (Kursus):** Et kursus består af et eller flere hold. Alle hold er forbundet til et kursus og kun et. Alle kurser skal have mindst et hold.
3. **Class (Hold):** Et hold består af en eller flere perioder. Alle perioder er forbundet til et hold og kun et. Alle hold skal have mindst en periode.
4. **Period (Periode)**
<br>
<br>
![Illustration af datastruktur](/Images/Kursusportalen.svg)

**De øvrige variable er bundet op på forskellige dele af det ovenfor beskrevne heiraki:**
- Antal pladser bestemmes på kursusniveau og holdene på kurset arver det tal.
- Holdstatus bestemmes på holdniveau. Da et kursus kan have flere hold, kan et kursus indeholde hold med alle typer af holdstatus (gennemført, aflyst osv.)
- Deltagerens status bestemmes på holdniveau (gennemført, på venteliste, tilmeldt)
- Deltagerens [evalueringsbesvarelse](#evalueringer)  er knyttet til en periode, da evalueringsskemaer tildeles perioder og et hold kan have flere perioder og der kan være forskellige eller det samme evalueringsskema på flere perioder under holdet. Derfor kan en deltager have svaret på mere end en evaluering i forbindelse med holdet. 
- Undervisere tildeles perioder. En periode kan godt have flere undervisere. En periode kan også have ingen underviser. Undervisere findes i tabellen 209 PeriodInstructor, ikke tabel 210 UserRole.
- [Evalueringsskemaer](#evalueringer) tildeles perioder og fordi et hold består af en eller flere perioder, så kan forskellige skemaer, være anvendt på det samme hold. Eksempelvis evaluering dag 1, dag 2 og afsluttende evaluering. 

### Evalueringer
Evalueringerne har deres eget entitetark i den samlede dokumentation. 

Et evalueringsskema ejes af et domæne. Skemaerne knyttes til kurser på periodeniveau. Derfor kan der være flere evalueringer på samme hold. Et kursus kan have flere hold og et hold kan have flere perioder.

En unik skemabesvarelse kan identificeres ud fra kombinationen af UserID, ClassID og SchemeID. Se tabel 307 ResultUser. Selve svarene på skemaet findes ud fra ResultID. Dette medfører desværre, at hvis samme skema er anvendt på flere perioder under samme hold, så kan vi ikke bestemme hvilken periode, besvarelsen vedrører. 

Spørgsmålene og de tilhørende svar kan inddeles i to kategorier: fritekst og skalaspørgsmål. Det bestemmes ud fra questionType på tilhørende questionID, hvilken type spørgsmål det er.  
- Tabellen 305 QuestionComment indeholder alle fritekstbesvarelserne. 
- Tabellen 304 QuestionOption indeholder svarmuligheder på skala-spørgsmålene. Den joines med tabel 306 QuestionAnswer, for at finde den/de muligheder, som brugeren har valgt.

**QuestionType**
- 1 = Kommentar. Brugeren angiver et fritekst et kommentar til spørgsmålet. Mappes til entitet 305 QuestionComment.
- 2 = Enten/eller. Brugeren kan vælge én option til spørgsmålet. Mappes til entitet 304 QuestionOption.
- 3 = Både/og. Brugeren kan vælge flere optioner til samme spørgsmål. Mappes til entitet 304 QuestionOption

### Brugere
Brugere i Kursusportalen oprettes på personniveau og ikke på ansættelsesniveau. 

Brugerne anonymiseres efter bestemte grænser:
- Inaktive interne brugere anonymiseres efter 1826 dage.
- Inaktive eksterne brugere anonymiseres efter 365 dage.
- Aktive eksterne brugere anonymiseres efter 365 dage uden aktivitet. 
- Profilløse brugerprofiler anonymiseres efter 365 dage.

Tabellen 101 UserPOE, indeholder oplysninger om brugeren ansættelsesforhold, men da brugeren tilmeldes kurser på personniveau ikke ansættelses, kan ansættelsen ikke bestemmes for brugere, med flere samtidige ansættelser. Der er mulighed for at vælge ansættelse ved tilmeldning, men denne funktion anvendes sjældent. Ved anvendelse findes værdien i tabellen 207 Courseparticipant kolonne OrgunitID.

### Views
I Data og Digitalisering har vi udarbejdet views ud fra de tabeller vi har modtaget fra ProOffice. Disse views anvendes i Power-BI. Lige nu er data fra Kursusportalen ikke forbundet til vores øvrige data. 

Der er lavet følgende views: [link til repository](https://github.com/DataOgDigitalisering/Kursusportal-dashboard/tree/main/views)
- dim_aktivitet. Dimensionstabel over kursusaktivitet
- dim_evaluering. Dimensionstabel over evalueringsbesvarelser
- dim_deltager. Dimensionstabel over deltagere
- dim_underviser. Dimensionstabel over undervisere
- fact_kursusdeltagelse. facttabel over kursusdeltagelse og evalueringsbesvarelser.
