# Opdatering af Kuben

<!-- Embed iFrame. word-doc: "CHRU_HRKube_opdatering.docx" på OneDrive-->
<center>
<iframe src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={ce5a2861-0de3-4324-a987-609d3764cb62}&amp;action=embedview&amp;wdPrint=0&amp;wdEmbedCode=0" width="1200" height="600" frameborder="0">This is an embedded <a target="_blank" href="https://office.com">Microsoft Office</a> document, powered by <a target="_blank" href="https://office.com/webapps">Office</a>.</iframe>
</center>

<!-- Udkommenteret til fordel for iFrame
## Generelt flow
![Flow](https://raw.githubusercontent.com/DataOgDigitalisering/dokumentation/master/Images/OpdateringKube.png)

## Kuben
Når der skal lægges ændringer op i selve kube-definitionen, så kontaktes CØK (Morten & Christopher), der så vil overføre Kube-definitionerne fra udviklingsserveren til produktionsserveren.
NB: Her er det vigtigt, at man sørger for at overføre evt. nye tabeller eller views fra udviklingsserveren til produktionsserveren, da Kuben ellers vil fejle, når den skal genberegnes. 

## Tabeller
Udover at en ny Kube-definition vil fejle i produktion uden en evt. ny tabel, så skal man være opmærksom på om en ny tabel bliver opdateret dagligt. 

Igen er det CØK, der skal sørge for at den nye tabel bliver er med i deres daglige SQL-job, der opdaterer alle tabellerne.
Tabellerne i udviklingsserveren opdateres ikke af sig selv. De opdateres manuelt ved behov ved at kopiere data fra produktionsserveren og overskrive den eksisterende data i udviklingsserveren. 
Script til at tjekke om tabeller er ens i PROD og UDV.
SØREN laver ændringer til COKP1, hvorefter Morten og Christopher overfører dem i deres daglige job til PROD.
## Views
Ændringer I View-definitioner gøres enkeltvis.  Morten og Christopher får at vide hvilket VIEW er ændret. De kopierer den nye VIEW-def fra UDV og lægger den over i PROD.
Script til at tjekke om VIEWS er ens i PROD og UDV.
## PowerBI
Opdateringer og udvikling i PowerBI bør først laves i udviklingsserveren, og så derefter lagt op i produktionsserveren. Der er adgang til at gøre dette uden CØK’s indblanding. Nogle gange kan mindre opdateringer dog fortages direkte i produktionsserveren, hvorfor at BI-filen i Udviklingsserveren med jævne mellemrum overskrives med filen fra produktionen.
-->
