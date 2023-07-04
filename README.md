# CHRU | Data & Rapportering

Vi er en sektion under enheden **Data og Digitalisering** i **Center for HR og Uddannelse (CHRU)**. Sektionen udstiller data og leverer ledelsesinformation til regionens personaleledere og topledelser i form af Power BI Dashboards. Tilmed understøtter sektionen andre dele af CHRU med dataanvendelse (intern styring, indsigter, erkendelser, mv.). Sektionen varetager også *postkassehenvendelser* internt fra hele regionen og fra eksterne parter (spørgsmål og aktindsigter fra politikere, og journalister). 
Sektionen har hovedsageligt tekniske medarbejdere med kompetencer i dataudtræk og datafremstilling og økonomimedarbejdere, samt ledelsesmedarbejdere til at understøtte disse.
<br>

<!-- PowerPoint: "Introduktion og onboarding til D&R"  -->
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={9400f055-6ddb-4862-aaa8-e3b2389a9bad}&amp;action=embedview&amp;wdAr=1.7777777777777777" height="587" width="1000" frameborder="0"></iframe>
</center>
<br>



# Introduktion til hjemmesiden

På denne wiki-side finder du:
- Dokumentation:
  - Dokumentation af ***HR Strategisk Dashboard* og *Lederdashboard***, hvor alle figurer og filtreringer er dokumenteret og beskrevet.
  - Dokumentation af ***CHRU_HRKube***, hvor kubens opbygning og measures er forklaret.
  - Dokumentation af de **views og tabeller** som kuben bygger på.
- Interne dokumenter:
  - Interne dokumenter som beskriver hvordan vi arbejder med **databaser, kuber og dashboards**.
  - Interne dokumenter som beskriver hvordan vi **versionsstyrer og dokumenterer vores arbejde**.
  - Beskrivelser af hvordan vi besvarer **postkassehenvendelser og laver dataudtræk**.

Nedenfor kan du se en liste over de produkter som vi udbyder, samt hvilke datakilder og miljøer de bygger på. Du kan også se en liste over de programmer som vi benytter i vores daglige arbejde.

# Vores produkter

Nedenstående tabel angiver hvilke datakilder og miljøer vores produkter bygger på. Hvis man ændrer i nogle af vores miljøer, skal man være opmærksom på hvilke produkter det kan påvirke.

<center>
<iframe src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={73422d8a-9d4c-4727-aa0e-5b24d601e81e}&amp;action=embedview" height="587" width="800" frameborder="0" seamless="yes"></iframe>
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
<iframe src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={c652f92d-8025-4f11-9b4c-3e0f0e0dadba}&amp;action=embedview&amp;wdEmbedCode=0&amp;wdPrint=0&wdToolbar=FALSE" height="730" width="1000" frameborder="0" seamless="yes"></iframe>
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



# Guids til programmer og software
Vi har her samlet nogle gode links og dokumenter, som beskriver hvordan man arbejder med de programmer og programmeringssprog, som vi benytter til daglig.

## Gode links og hjemmesider
- [https://www.sqlbi.com](https://www.sqlbi.com/), beskriver mange vigtige aspekter af SQL og Power BI, og er et super sted at finde information om alt fra filterkontekt i DAX til opbygning af datamodeller.

## Kurser og andre dokumenter
<!-- Embed iFrame. PowerPoint: "SQL-kursus.pptx" på OneDrive-->
{::options parse_block_html="true" /}
<details><summary markdown="span">Slides til SQL-kursus</summary>
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/stefan_sajin-henningsen_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={ee7ec7a1-d13c-4855-a459-c1717f9aa646}&amp;action=embedview&amp;wdEmbedCode=0&amp;wdPrint=0&wdToolbar=FALSE" height="587" width="1000" frameborder="0" seamless="yes"></iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>

