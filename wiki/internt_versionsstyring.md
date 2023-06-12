# Versionsstyring af kuben
Vi benytter GitHub til versionsstyring. Dette er en guide til hvordan vi arbejder parallelt på kuben og implementerer vores ændringer via. GitHub. **Alle ændringer som laves på *CHRU_HRKube* i udvikling og produktion skal ske gennem GitHub**. Vi laver kun ændringer direkte i *CHRU_HRKube* hvis det er akutte ting som ikke kan vente. Følgende figur illustrerer arbejdsprocessen med GitHub. De forskellige skridt er beskrevet mere detaljeret nedenfor.
<center><br><img src="Images/BillederInterVersionsstyring/modelVersionsstyring.PNG" height="300" style="vertical-align:middle"/></center>



## Koble sin computer til GitHub
Versionsstyring af kuben sker i repository'et [*CHRU_HRKube*](https://github.com/DataOgDigitalisering/CHRU_HRKube). Når man vil versionsstyre med GitHub, skal man kopiere dette repository ned på ens egen computer, lave ændringerne lokalt, og herefter sende ændringerne op til GitHub igen.
For at kunne arbejde med GitHub lokalt på ens computer skal man gøre følgende:
- Download *GitHubDesktop 2.9.8.0* eller en nyere version fra softwareshoppen. 
<br><img src="Images/BillederInterVersionsstyring/1GitHubSoftwareshop.PNG" height="130" style="vertical-align:middle"/>
- Start *GitHubDesktop* på din computer.
- Klik på "*options*" og log ind med din GitHub-konto.
<br><img src="Images/BillederInterVersionsstyring/2GitHubForbindTilKonto.png" height="160" style="vertical-align:middle"/>
- Klik på feltet øverst i højre hjørne, klik på "*add*" og klik "*clone repository...*". Du kan nu vælge det repository som du gerne vil kopiere ned på din computer. Vælg "*CHRU_HRKube*" under "*DataOgDigitalisering*". **Det er en god idé at gemme mappen på skrivebordet og ikke på et af de online drev**. Ellers kan det tage en del tid at gemme kuben, når vi senere benytter funktionen "*SaveToFolder*".
<br><img src="Images/BillederInterVersionsstyring/3GitHubCloneRepo.png" height="150" style="vertical-align:middle"/>

Du er nu klar til at arbejde med GitHub lokalt på din computer. Alle disse skridt er også beskrevet i GitHub's egen dokumentation som du kan finde her [*https://docs.github.com/en/desktop*](https://docs.github.com/en/desktop).

## Sæt en lokal kube og branch op
Vi laver som udgangspunkt ikke ændringer direkte i *CHRU_HRKube* på produktion eller udvikling. Hvis man ønsker at ændre noget, skal det ske ved at man laver ændringerne i en separat kube og herefter *merger* den med vores *CHRU_HRKube* via. GitHub.
For at lave ændringer i en separat kube skal man gøre følgende:
- På vores analysis server i udvikling har vi nogle ekstra kuber. Her kan man få sin egen kube og omdøbe den til noget som giver mening f.eks. "*ProjektVersionsstyring*".

- Gå ind i *GitHubDesktop* og vælg repository'et "*CHRU_HRKube*" og branchen *Udvikling* og klik "*New Branch*".
<br><img src="Images/BillederInterVersionsstyring/4GitHubNewBranch.png" height="150" style="vertical-align:middle"/>

- Kald den det samme som det din private kube hedder, og sig at den skal være "*based on Udvikling*". Hvis du ikke ser muligheden *Udvikling* er det fordi du ikke "står" på branchen *Udvikling*.
<br><img src="Images/BillederInterVersionsstyring/5GitHubNewBranchCreate.png" height="250" style="vertical-align:middle"/>

- Nu skulle der gerne stå "*Current Branch: ProjektVersionsstyring*" i toppen.
- Ved at højreklikke på "*Current Repository*" kan du let finde den mappe hvor repository'et ligger.
<br><img src="Images/BillederInterVersionsstyring/6GitHubShowInExplorer.png" height="200" style="vertical-align:middle"/>


## Deploy tabular model fra GitHub til kuben
Du kan nu deploye den tabulare model fra *CHRU_HRKube* over til din egen kube. Herefter kan du lave ændringer og gemme dem på din nye branch. Dette gøres på følgende måde:
- Åben *Tabular Editor* og importer din tabulare model ved at bruge "*Open from folder*".
<br><img src="Images/BillederInterVersionsstyring/7TabularEditorÅbenFromFolder.png" height="200" style="vertical-align:middle"/>
- Vælg den mappe som dit respository ligger i. **Det er vigtigt at du har valgt den rigtige branch inde i *GitHubDesktop*.** Ellers vil du komme til at importere en tabular model fra en forkert branch. Mappen skal indeholde de fire mapper *dataSources*, *relationships*, *roles* og *tables*. 
<br><img src="Images/BillederInterVersionsstyring/8TabularEditorVælgMappe.png" height="300" style="vertical-align:middle"/>

- Du kan nu deploye modellen til din egen kube. **Når du deployer modellen skal du fravælge *Data Source* og *Roles* (husk også at fravælge *Deploy Role Memebers*), da de kan variere fra kube til kube, og vi ikke ønsker at ændre dem.** Du kan herefter processere den i "*Server Management Studio*".

## Gem dine ændringer i Git
Når du har arbejdet på din model og lavet ændringer i *Tabular Editor* kan du gemme dem på din branch, dette gøres på følgende måde:
- Åben *GitHubDesktop* og vælg den branch som du arbejder på.
- Åben mappen som dit respository ligger i og slet alt indhold i mappen så den er tom. Hvis du kan se en .git fil skal du IKKE slette den.
<br><img src="Images/BillederInterVersionsstyring/9GitHubSletAltIMappe.png" height="250" style="vertical-align:middle"/>

- I Tabular Editor åbner du din egen kube.
- Herefter kan du gemme din tabulare model ved brug af "*Save To Folder*" og vælge den mappe som dit repository ligger i.
<br><img src="Images/BillederInterVersionsstyring/10TabularEditorSaveToFolder.png" height="190" style="vertical-align:middle"/>

- I GitHubDesktop kan du nu se alle de ændringer som du har lavet
<br><img src="Images/BillederInterVersionsstyring/11GitHubVisÆndringer.png" height="300" style="vertical-align:middle"/>

- Hvis du er tilfreds med ændringerne kan du skrive en lille tekst nederst i venstre hjørne og klikke "*Commit to ...*".
Nu er ændringerne gemt på din branch. Noget af dette er også beskrevet i Tabular Editor's egen dokumentation som kan ses her [https://docs.tabulareditor.com/onboarding/parallel-development.html](https://docs.tabulareditor.com/onboarding/parallel-development.html).

Du kan løbende gemme dine ændringer over i Git ved at gentage disse skridt.

## Få ændringerne op til GitHub
Nu er du klar til at få ændringer op til GitHub, hvor alle i teamet kan tilgå dem!
- I *GitHubDesktop* vælger du "*CHRU_HRKube*" under "*Current Repository*".
- Herefter kan du klikke på "*Publish Branch*". Dine ændringer og branch er nu blevet skubbet op til GitHub.
<br><img src="Images/BillederInterVersionsstyring/12GitHubPublishBranch.png" height="60" style="vertical-align:middle"/>

- Under [*https://github.com/DataOgDigitalisering/CHRU_HRKube*](https://github.com/DataOgDigitalisering/CHRU_HRKube) vil du nu kunne se den nye branch samt alle de ændringer du har lavet. Du kan nu lave flere ændringer lokalt på din computer og "pushe" dem op løbende.
<br><img src="Images/BillederInterVersionsstyring/13GitHubAlleBrnaches.png" height="250" style="vertical-align:middle"/>

## Få ændringerne over på udvikling og produktion
For at få ændringer over i udvikling skal din egen branch *merges* med udvikling. Dette gøres ved at lave en *Pull-request*:
- Klik på "*Pull-request*" i toppen og vælg "*New Pull Request*".
<br><img src="Images/BillederInterVersionsstyring/14GitHubNewPullRequest.png" height="200" style="vertical-align:middle"/>

- Sæt den til at merge din egen branch med "*Udvikling*".
<br><img src="Images/BillederInterVersionsstyring/15GitHubPullRequestBranches.png" height="120" style="vertical-align:middle"/>

- **Man skal som udgangspunkt altid koble en *Pull-request* til et *Issue*.** Dette gøres f.eks. ved at skrive #23 hvis det er Issue nr. 23 som man arbejder på. Hvis der ikke er oprettet et Issue skal dette først gøres. SE TODO for mere om dette.
- Du har nu lavet en ny *pull-request*. En gatekeeper vil herefter se ændringerne igennem og *approve* dem.
- Når dette er gjort vil ændringer kommer over på branchen "*Udvikling*". Og man kan herefter deploye dem til *CHRU_HRKube* i udvikling ved brug af *TabularEditor* og *GitHubDesktop*.
- For at få ændringerne over i produktion, merger vi *udvikling* og *produktion* i GitHub. Herefter kan man deploye ændringerne til *CHRU_HRKube* i produktion ved brug af *TabularEditor* og *GitHubDesktop*.

## Rydde op efter sig
Når man har lavet alle ændringer og de er kommet over på udvikling skal man gøre følgende:
- Slette sin branch i *GitHub* og evt. i *GitHubDesktop*.
- Omdøbe sin kube til "*CHRU_LedigKube1*" eller noget lignende.

- Når man først har klonet repository'et ned på ens egen computer, kan man bare benytte knappen "*Fetch origin*" til at opdatere sit lokale repository, så det er up-to-date med de ændringer som laves af andre i GitHub.
<br><img src="Images/BillederInterVersionsstyring/16GitHubFetch.png" height="120" style="vertical-align:middle"/>

## Praktisk information om opdatering af kuben
- Gatekeeper ser hver uge alle pull-requests igennem og skriver ændringerne ned. 
- Dette deles på onsdagsmødet så alle er up-to-date med de ændringer som er foretaget i *CHRU_HRKube*. 
- Vi opdaterer produktion umiddelbart efter ændringerne er blevet testet i udvikling. Ved større ændringer hvor der tilføjes tabeller el. lign. kan det tage længere tid at få over i produktion.

# Versionsstyring af views TODO

