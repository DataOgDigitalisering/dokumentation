# CHRU | Data & Rapportering

Vi er en sektion under enheden **Data og Digitalisering** i **Center for HR og Uddannelse (CHRU)**. Sektionen udstiller data og leverer ledelsesinformation til regionens personaleledere og topledelser i form af Power BI Dashboards. Tilmed understøtter sektionen andre dele af CHRU med dataanvendelse (intern styring, indsigter, erkendelser, mv.). Sektionen varetager også *postkassehenvendelser* internt fra hele regionen og fra eksterne parter (spørgsmål og aktindsigter fra politikere, og journalister). 
Sektionen har hovedsageligt tekniske medarbejdere med kompetencer i dataudtræk og datafremstilling og økonomimedarbejdere, samt ledelsesmedarbejdere til at understøtte disse.
<br>

<!-- PowerPoint: "Introduktion og onboarding til D&R"  -->
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={3f4e8ec2-63e5-4933-8b95-28f6f4caac35}&amp;action=embedview&amp;wdAr=1.7777777777777777" width="800" height="587" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> presentation, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>
<br>

# Introduktion til hjemmesiden

På denne wiki-side finder du:
- Dokumentation:
  - Dokumentation af ***CHRU_HRKube***, hvor kubens opbygning, temaer og measures er forklaret.
  - Dokumentation af de **views og tabeller** som kuben bygger på.
- Interne dokumenter:
  - Interne dokumenter som beskriver hvordan vi arbejder med **databaser, kuber og dashboards**.
  - Interne dokumenter som beskriver hvordan vi **versionsstyrer og dokumenterer vores arbejde**.
  - Beskrivelser af hvordan vi besvarer **postkassehenvendelser og laver dataudtræk**.

Nedenfor kan du se en liste over de produkter som vi udbyder, samt hvilke datakilder og miljøer de bygger på. Du kan også se en liste over de programmer som vi benytter i vores daglige arbejde.

# Ansvarlige for temaer
Følgende dokument angiver hvem der er ansvarlige for hvilke temaer, dvs. hvem der står for at dokumentere temaet og vedligeholde dokumentationen efterfølgende. Det angiver også hvilke tabeller og measures som hører under hvert tema.

<center>
<iframe width="1200" height="587" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={cc0acbe9-7029-4db0-8d40-b5ef133133fb}&action=embedview&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdDownloadButton=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>

# Vores produkter

Nedenstående tabel angiver hvilke datakilder og miljøer vores produkter bygger på. Hvis man ændrer i nogle af vores miljøer, skal man være opmærksom på hvilke produkter det kan påvirke.

<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={384b395b-9001-4165-8366-f157c975223b}&amp;action=embedview" width="1000" height="500" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> document, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>
<br>


# Software som vi benytter
Følgende software er en forudsætning og kan findes i <a href="https://softwarecentral.regionh.top.local/Shop" target="_blank">Softwareshoppen</a>. 

Hav altid seneste version af Power BI Desktop installeret for at sikre nyeste og kompatibel funktionalitet med rapportserver. For versioner af øvrig software spørg en kollega, hvad de bruger.

- Microsoft SQL Server Management Studio
- Power BI desktop
- SQL Server Data Tools Bundle
  - Dax Studio
  - Tabular Editor
<br>


# Dataadgang
Nedenstående dokument beskriver hvordan du søger om adgang til data. Det er selvfølgelig vigtigt, at du har de nødvendige adgange, hvis du vil arbejde med data og lave dataudtræk.
<!-- Embed iFrame. word-doc: "Guide til bestilling af adgange.docx" på OneDrive-->
{::options parse_block_html="true" /}
<details><summary markdown="span">Guide til bestilling af dataadgange</summary>
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={9e94c646-b5ab-466e-89e9-0af964b2d493}&amp;action=embedview&amp;wdEmbedCode=1&amp;wdPrint=1" width="1000" height="700" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> document, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>

<!-- ØVELSE -->
{::options parse_block_html="true" /}
<details><summary markdown="span">**ØVELSE - KONTROL AF DATAADGANGE** <img src="Images/icons_ref/icon_git.png" height="35" width="35"></summary>
  
> - Følg <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_dataadgange.sql" target="_blank">**dette link til SQL-script**</a>.
> - Åbn og eksekver scriptet i SQL Server Management Studio. Kørslen kan tage >20 minutter og returnerer en tabel, der beskriver dine adgange. Spørg en kollega om du har de adgange, du har brug for.

</details>
{::options parse_block_html="false" /}



# Guides til programmer og software
Vi har her samlet nogle gode links og dokumenter, som beskriver hvordan man arbejder med de programmer og programmeringssprog, som vi benytter til daglig.

## Gode links og hjemmesider
- [https://www.sqlbi.com](https://www.sqlbi.com/), beskriver mange vigtige aspekter af SQL og Power BI, og er et super sted at finde information om alt fra filterkontekt i DAX til opbygning af datamodeller.
- [https://www.youtube.com/@GuyInACube](https://www.youtube.com/@GuyInACube) har en hel del videoer som beskriver mange centrale dele af Power BI, kuber og datamodeller.
- [https://learn.microsoft.com/en-us/dax/](https://learn.microsoft.com/en-us/dax/) DAX dokumentation fra Microsoft
## Kurser og andre dokumenter
<!-- Embed iFrame. PowerPoint: "SQL-kursus.pptx" på OneDrive-->
{::options parse_block_html="true" /}
<details><summary markdown="span">Slides til SQL-kursus</summary>
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={e064786b-ec9d-4478-9696-198b15f134a8}&amp;action=embedview&amp;wdAr=1.7777777777777777" width="1200" height="700" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> presentation, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>

