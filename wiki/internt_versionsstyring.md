# Versionsstyring af kuben - UNDER UDVIKLING
Vi benytter GitHub til versionsstyring. Dette er en guide til hvordan vi arbejder parallelt på kuben og implementerer vores ændringer via. GitHub. **Alle ændringer som laves på *CHRU_HRKube* i udvikling og produktion skal ske gennem GitHub**. Man må kun ændre direkte i *CHRU_HRKube* hvis der er akutte ændringer som ikke kan vente. Følgende figur illusterer arbejdsprocessen med GitHub. De forskellige skridt er beskrevet nedenfor.
<center><br><img src="Images/BillederInterVersionsstyring/modelVersionsstyring.PNG" height="300" style="vertical-align:middle"/></center>



## Koble sin computer til GitHub
Versionsstyring af kuben sker i repository'et [*CHRU_HRKube*](https://github.com/DataOgDigitalisering/CHRU_HRKube). Den letteste måde at arbejde med GitHub er at kopiere denne folder ned på ens egen computer, lave ændringerne, og herefter sende ændringerne op til GitHub igen.
For at kunne arbejde med GitHub, lokalt på ens computer skal man gøre følgende:
- Download *GitHubDesktop 2.9.8.0*, eller en nyere version, fra softwareshoppen. 
<br><img src="Images/BillederInterVersionsstyring/1GitHubSoftwareshop.PNG" height="130" style="vertical-align:middle"/>
- Start "GitHubDesktop" på din computer.
- Klik på "options" og log ind med din GitHub-konto.
<br><img src="Images/BillederInterVersionsstyring/2GitHubForbindTilKonto.png" height="160" style="vertical-align:middle"/>
- Klik på feltet øverst i højre hjørne, klik på "*add*" og klik "*clone repository...*". Du kan nu vælge den folder du gerne vil kopiere ned på din computer. Vælg "CHRU_HRKube" under "DataOgDigitalisering". OBS: Det er en god idé at gemme mappen på skrivebordet f.eks. og ikke på et af de online drev. Ellers kan det tage en del tid at gemme kuben over når vi benytter funktionen "SaveToFolder" senere.
<br><img src="Images/BillederInterVersionsstyring/3GitHubCloneRepo.png" height="150" style="vertical-align:middle"/>

Du er nu klar til at lave ændringer på kuben lokalt på din computer. Alle disse skridt er også beskrevet i GitHub's egen dokumentaiton som du kan finde her [https://docs.github.com/en/desktop](https://docs.github.com/en/desktop).

## Sæt lokal kube og branch op
Man må ikke lave ændringer direkte i produktion eller udvikling. Hvis man ønsker at ændre noget skal det ske ved at man laver ændringerne i en privat kube, og herefter "pusher" og "merger" det med udvikling og produktion via. GutHub.
For at lave ændringer i en lokal kube skal man gøre følgende:
- På vores analysis server i udvikling har vi nogle ekstra kuber. Her kan man få sin egen kube og omdøbe den til noget som giver mening f.eks. "ProjektVersionsstyring".

- Gå ind i GitHub Desktop og vælg repositoriet "CHRU_HRKube" og klik "newBranch".
<br><img src="Images/BillederInterVersionsstyring/4GitHubNewBranch.png" height="150" style="vertical-align:middle"/>

- Kald den det samme som din private kube hedder og sig at den skal bygge på "udvikling".
<br><img src="Images/BillederInterVersionsstyring/5GitHubNewBranchCreate.png" height="250" style="vertical-align:middle"/>

- Nu skulle der gerne stå "Current Branch: "ProjektVersionsstyring" i toppen.
- Ved at højreklikke på "Current Repository" kan du let finde den mappe hvor repositoriet er.
<br><img src="Images/BillederInterVersionsstyring/6GitHubShowInExplorer.png" height="200" style="vertical-align:middle"/>


## Deploy datamodel fra Git til kuben
Du kan nu deploye den tabulare model til din private kube, lave ændringer på den og gemme dem på din nye branch. Dette gøres på følgende måde:
- Åben Tabular Editor og importer din tabulære model ved at bruge "Open from folder", og vælg den folder som din branch lægger i. Det er vigtigt at du har valgt den rigtige branch inde i GitHubDesktop. Ellers vil du komme til at importere en forkert branch til TabularEditor.
<br><img src="Images/BillederInterVersionsstyring/7TabularEditorÅbenFromFolder.png" height="200" style="vertical-align:middle"/>
<br><img src="Images/BillederInterVersionsstyring/8TabularEditorVælgMappe.png" height="300" style="vertical-align:middle"/>

- Du kan nu deploye modellen til din private kube, og herefter processere den i "Server Management Studio".

## Gem dine ændringer i Git
Når du har arbejdet på din model og lavet ændringer i Tabular Editor kan du gemme dem på din branch, dette gøres på følgende måde:
- Åben GitHubDesktop og vælg den branch som du arbejder på.
- Åben mappen hvor branchen er og slet alt indhold i mappen så den er tom. Hvis du kan se en .git fil skal du IKKE slette den.
<br><img src="Images/BillederInterVersionsstyring/9GitHubSletAltIMappe.png" height="250" style="vertical-align:middle"/>

- I Tabular Editor åbner du den model som du gerne vil gemme over fra din egen kube.
- Herefter kan du gemme den ved brug af "Save To Folder" og vælge den mappe som din branch er i.
<br><img src="Images/BillederInterVersionsstyring/10TabularEditorSaveToFolder.png" height="190" style="vertical-align:middle"/>

- I GitHubDesktop kan du nu se alle de ændringer du har lavet
<br><img src="Images/BillederInterVersionsstyring/11GitHubVisÆndringer.png" height="300" style="vertical-align:middle"/>

- Hvis du er tilfreds med ændringerne kan du skrive en lille tekst nederst i venstre hjørne og klikke "Commit to ..."
Nu er ændringerne gemt på din branch. Noget af dette er også beskrevet i Tabular Editor's egen dokumentation [https://docs.tabulareditor.com/onboarding/parallel-development.html](https://docs.tabulareditor.com/onboarding/parallel-development.html).

## Få ændringerne op til GitHub
Nu er vi klar til at få ændringer op til GitHub hvor alle kan tilgå dem.
- I GitHubDesktop vælger "CHRU_HRKube" under "Current Repository".
- Herefter kan du klikke på "Publish Branch". Dine ændringer er nu blevet skubbet op til GitHub.
<br><img src="Images/BillederInterVersionsstyring/12GitHubPublishBranch.png" height="60" style="vertical-align:middle"/>

- Under (https://github.com/DataOgDigitalisering/CHRU_HRKube)[https://github.com/DataOgDigitalisering/CHRU_HRKube] vil du nu kunne se den nye branch samt alle de ændringer man har lavet. Du kan lave ændringer lokalt og "pushe" dem op løbende.
<br><img src="Images/BillederInterVersionsstyring/13GitHubAlleBrnaches.png" height="250" style="vertical-align:middle"/>

## Få ændringerne over på udvikling og produktion
For at få ændringer over i udvikling skal ens egen branch "merges" med udvikling. Dette gøres ved at lave en pull-request:
- Klik på "Pull-request" i toppen og vælg "New Pull Request".
<br><img src="Images/BillederInterVersionsstyring/14GitHubNewPullRequest.png" height="200" style="vertical-align:middle"/>

- Sæt den til at merge din egen branch med "Udvikling".
<br><img src="Images/BillederInterVersionsstyring/15GitHubPullRequestBranches.png" height="120" style="vertical-align:middle"/>

- I beskrivelsen af din pull-reqeust skal du koble den til et Issue. Dette gøres ved at skrive #23 hvis det er Issue nr. 23 som man arbejder på.
- Hefter vil den stå under "pull-request". En af gatekeeperne vil herefter se ændringerne igennem og "approve" den.
- Når dette er gjort vil ændringer kommer over på branchen "Udvikling". Og man kan så deploye dem til vores udviklings-kube ved brug af Tabular Editor og GitHubDesktop.
- Når man først har klonet repositoriet ned på ens egen computer kan man bare benytte knappen "Fetch origin" for at opdatere ens lokale repository, så det svarer til det som ligger på GitHub.
<br><img src="Images/BillederInterVersionsstyring/16GitHubFetch.png" height="120" style="vertical-align:middle"/>


##Rydde op efter sig
Når man har lavet alle ændringer, og det er kommet over på udvikling skal man gøre følgende:
- Slette sin branch i GitHub og evt. i GitHubDesktop.
- Omdøbe sin kube til "CHRU_LedigKube1" eller noget lignende.

Ændringerne vil komme over i produktion næste gang man flytter kopiere kuben fra udvikling over i produktion.

