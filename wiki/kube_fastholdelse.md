# Fastholdelse
Nedenfor er vigtige tanker og overvejelser vedrørende temaet "Fastholdelse" beskrevet.

## Fanerne i fastholdelses-temaet
Fastholdelsestemaet indeholder fanen ”Fastholdelse”, som bl.a. viser antallet af fratrådte og afgangsrater på tværs af organisations- og stillingshierarkier samt fastholdelseskurver. Temaet indeholder desuden fanen ”Mobilitet”, som viser intern medarbejdermobilitet på tværs af hospitaler og virksomheder i regionen.

## Definitioner og afgrænsninger
-	Temaet ”Fastholdelse” skal bidrage til at give indsigt i organisationens evne til at fastholde medarbejdere over tid, og er derfor afgrænset til at omfatte ”ikke-forventelige” fratrædelser, dvs. fratrædelser som på den ene eller anden måde ikke kan siges at være planlagt som følge af fx uddannelsesforløb, pensionsfratrædelse m.m. Midlertidigt ansatte kan også siges at være forventelige fratrædelser, men disse kan ikke afgrænses i lønsystemet og er derfor inkluderet.
-	Den primære indikator til at måle organisationens fastholdelsesevne er afgangsraten, som angiver, hvor stor en andel af de medarbejdere, som var ansat primo en 12 mdr. periode, der er fratrådt i slutningen af samme periode. Afgangsrate benævnes også undertiden personaleomsætning, men sidstnævnte opgøres ofte ved også at tage højde for andelen af tiltrædelser i perioden.
-	Populationen er afgrænset til at omfatte fastansat personale, dvs. månedslønnede. Timelønnede og elever er ikke inkluderet som følge af deres løsere tilknytning til arbejdsstedet. Uddannelseslæger og pensionsfratrædelser er som udgangspunkt fravalgt, da disse personalegrupper er atypiske i forhold til øvrige fratrædelser, men kan dog tilvælges via filtre.
-	Fastholdelses-temaet viser også andelen af rokeringer til anden virksomhed i forhold til alle fratrædelser de seneste afsluttede 12 mdr. viser. Oversigten inkluderer udelukkende månedslønnede medarbejdere, som var ansat primo 12 mdr. perioden. Personer, der både tiltræder og fratræder i løbet af perioden, er således ikke medregnet. Dette er særligt vigtigt at erindre, idet matrixen under mobilitets-fanen også inkluderer personer, der til- og fratræder indenfor 12 mdr. perioden.

## Bemærkninger til views og measures
-	Measures, som anvendes i temaet, er i stor udstrækning baseret v_DimAnsættelse, herunder især kolonnen med hændelser.
-	Det er muligt at filtrere på følgende fratrædelsestyper: "Til/fra Region Hovedstaden", "Mellem institutioner" og ”Mellem” afdelinger”. Fratrædelsestypen "Afbrudt ansættelse på under 3 mdr." er indført med henblik på at se bort fra fratrædelser ud af regionen, hvor personen meget hurtigt bliver genansat (indenfor 3 mdr.). Der kan på denne måde ses bort fra fx stillingsskift, hvor der ikke er 100% tidsmæssig kontinuitet og som derfor vil give en højere afgangsraterne, som ikke reelt afspejler virkeligheden.
-	De filtre, som anvendes til filtrering af ledere og uddannelseslæger, er baseret på to kolonner i v_DimStilling. Begge kolonner er baseret på hard-kodning af stillingskoder, og bør regelmæssigt genbesøges mhp. vedligeholdelse.
-	Measuret Fastholdelseskurver3År beregner fastholdelseskurverne og er det mest komplekse measure i kuben. Measuret beregner den kumulerede sandsynlighed som funktion af tiden i år for at en medarbejder indenfor en givet fagstillingsgruppe forlader sin stilling. Sandsynligheden er baseret på de sidste tre års fratrædelser.
Det kan overvejes at basere measuret Kaplan-Meier-estimatoren, som bl.a. anvendes indenfor medicinsk forskning.
-	Pas på med ikke at forveksle afgangsrate med afgangsrate for nyansatte (første års afgangsrate), som indgår i onboarding-temaet.
-	Vær opmærksom på at både afgangsrater og fastholdelseskurver skal håndteres med varsomhed ved små populationer, og der kan derfor forekomme relativt store udsving ved filtrering.
-	Measuret RokeringerSeneste12mdrAntal beregner antallet af rokeringer til anden institution indenfor de sidste 12 afsluttede mdr. Bemærk, at measuret er ”låst” og ikke reagerer på filtret til bestemmelse af fratrædelsestype. Fratrædelsestypen ”Mellem afdelinger” er ikke inkluderet i measuret.

# Tabeller og kolonner
Nedenfor er tabeller og kolonner beskrevet. Alle views som CHRU_HRkuben bygger på kan ses [*her*](https://github.com/DataOgDigitalisering/versionsstyringViews/tree/Produktion/viewFolder).

<b>Tabeller</b>
<center>
<iframe width="1200" height="400" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Fastholdelse_Tabeller&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>
 
<b>Kolonner</b>
<center>
<iframe width="1200" height="300" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Fastholdelse_Kolonner&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>

# Measures
Nedenfor er de measures som knytter sig til temaet beskrevet. Alle measures som ligger i CHRU_HRkuben kan også ses [*her*](https://github.com/DataOgDigitalisering/CHRU_HRKube/tree/produktion/tables/_Measures/measures).

<b>Measures</b>
<center>
<iframe width="1200" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={8d5cf238-e8c7-40f1-bf4f-139fc065219d}&action=embedview&wdAllowInteractivity=False&Item=Fastholdelse_Measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
