# Introduktion
Denne side indeholder ekstra ting som der ikke var plads til andre steder. Noget af dette skal slettes på et tidspunkt, andet skal flyttes.


## Farvetema
<!-- Embed iFrame. PowerPoint: "One pager - Design guidelines til rapporter i FLIS" på OneDrive-->
{::options parse_block_html="true" /}
<details><summary markdown="span">One pager — Design guidelines til rapporter i FLIS</summary>
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={c5fed6c6-8b5b-4dcd-9a50-de824a76d4dc}&amp;action=embedview&amp;wdAr=1.7777777777777777" width="900" height="600" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> presentation, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>  
<br>
</details>
{::options parse_block_html="false" /}


# Ekstra øvelser
## ØVELSE - KONTROL AF DATAADGANGE <img src="Images/icons_ref/icon_git.png" height="35" width="35">

> - Følg <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_dataadgange.sql" target="_blank">**dette link til SQL-script**</a>.
> - Åbn og eksekver scriptet i SQL Server Management Studio. Kørslen kan tage >20 minutter og returnerer en tabel, der beskriver dine adgange. Spørg en kollega om du har de adgange, du har brug for.



## ØVELSE - BRUGERSTYRING <img src="Images/icons_ref/icon_git.png" height="35" width="35">

> - Hvem er din sektionsleder og hvilke(n) rolle(r) er denne tildelt i SD? 
> - På hvilket organisatorisk niveau (NY-niveau) er disse gældende?
> - Hvilke SD-rolle har du selv?
> - Givet at du ikke er leder, hvorfor kan du se data i HR Lederdashboardet?
> - Hvad skal vi ændre, hvis flere SD-grupper skal kunne anvende HR Lederdashboardet?
>  
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_brugerstyring.sql" target="_blank">**løsningsforslag**</a>.



## ØVELSE - KOLLEGAER <img src="Images/icons_ref/icon_git.png" height="35" width="35">

> Kun vha. data fra CHRU_HRKube lav en tabel indeholdende alle dine kollegaer i sektionen. Tabellen skal indeholde en og kun en række pr. person med en af statuskoderne 0, 1 eller 3. Maksimalt ét søgekriterie må være hard-codet, fx et navn eller et id fra organisationshierakiet.
> Sammensæt kolonnerne:
>
> | Navn | Fødselsdato | Alder | Stilling | Hovedstillingsgruppe | Sektion | Enhed | Statuskode | Anciennitet |
>
> - Hvad er aldersfordelingen blandt dine kollegaer
> - Hvilke funktioner har I ansat i sektionen?
> - Hvor længe har folk været ansat?
>
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_kollegaer.sql" target="_blank">**løsningsforslag**</a>.



## ØVELSE - PERSONALESAMMENSÆTNING <img src="Images/icons_ref/icon_git.png" height="35" width="35">

Beregn vha. kuben:
> - Hvor mange måneds- og timelønnede er ansat i sektionen dags dato med statuskode 0, 1 eller 3?
> - Hvor mange årsværk arbejdes i sektionen?
> - Hvordan er denne fordelingen mellem sektioner og jobstillinger?
> - Passer din udregning med hvad HR Lederdashboardet viser?
>
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_personale.sql" target="_blank">**løsningsforslag**</a>.



## ØVELSE - FRAVÆRSTYPER <img src="Images/icons_ref/icon_git.png" height="35" width="35">
   
> I CHRU_HRKube anvendes i tabellen v_DimLønartFravær en anden gruppering af fraværstyper (L2Name), end den gruppering SD bruger (LOENARTTXT).
>
> - Gør rede for ligheder og forskelle. 
> - Hvad er grunden til, at der i CHRU_HRKube anvendes en anden gruppering?
>
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_frav%C3%A6rstyper.sql" target="_blank">**løsningsforslag**</a>.



## ØVELSE - FRAVÆR <img src="Images/icons_ref/icon_git.png" height="35" width="35">
  
> - Beregn sektionens fravær (fraværsdage og fuldtidsdage) i de seneste 12 hele måneder fordelt på enheder
> - Sammenlign med HR Lederdashboarder
>
> Se <a href="https://github.com/DataOgDigitalisering/FortroligInformation/blob/main/Exercises/ex_fravær.sql" target="_blank">**løsningsforslag**</a>.


# Gamle noter som gemmes til senere
- Overvej hvor/hvad vi kan trække ift. versionsstyring/vedligeholdelse:
- SSMS: 
  - Database: view-definitioner, oversigt over tabeller og views, hvor de bruges osv.
  - Kuben: billede af model og relationer – Nicolai viste dette
- Tabular Editor
  - Hvordan tabeller og measures bygger på hinanden – Nicolai viste Excel-dok
- Power BI
  - Hvor measures bruges, hvilke der ikke bruges osv. – Nicolai nævnte kort at dette (måske…) var en mulighed

**Aftaler for ændringer i CHRU_HRKube:**
- Roller. Hvem gør/har ansvar for hvad?
  - SQL, Dax, Git, dok
  - Intervaller
 

**Kontrol-scripts:**
- Til hvad? Afdæk behov


**Oprydning:**
- Hvordan implementerer vi vedtaget nomenklatur?
- Prioriter. Hvad kan vi leve med?
  - performance vs æstetik
  - slette ubrugte tabeller/kolonner vs ændre æ ø å 

- Vigtigt med afsnit om hvordan man bygger nye temaer op, så vi navngiver konsistent osv.
- Vigtigt at have et sted hvor man beskriver hvordan man filtrerer på stilling og DimOrganisation (til folk som skal bygge nye dashboards f.eks.)

