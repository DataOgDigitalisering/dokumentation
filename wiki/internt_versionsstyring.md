# Verionsstyring af kuben
Vi benytter GitHub til versionsstyring. Dette er en guide til hvordan vi arbejder på kuben og implementerer vores ændringer.

## Koble ens computer til GitHub
Versionsstyring af kuben sker i folderen [*CHRU_HRKube*](https://github.com/DataOgDigitalisering/CHRU_HRKube). Den letteste måde at arbejde med GitHub er at kopiere denne folder ned på ens egen computer, lave ændringerne, og herefter sende ændringerne op til GitHub.
For at kunne arbejde med GitHub på ens computer skal man gøre følgende:
- Download *GitHubDesktop 2.9.8.0*, eller en nyere version, fra softwareshoppen. 
- Start "GitHubDesktop" på din computer.
- Klik på "options" og log ind med din GitHub-konto.
- Klik på feltet øverst i højre hjørne, klik på "*add*" og klik "*clone repository...*". Du kan nu vælge den folder du gerne vil kopiere ned på din computer. Vælg "CHRU_HRKube" under "DataOgDigitalisering". OBS: Det er en god idé at gemme mappen på skrivebordet f.eks. og ikke på et af de online drev. Ellers kan det tage en del tid at gemme kuben over når vi benytter funktionen "SaveToFolder" senere.

Du er nu klar til at lave ændringer på kuben lokalt på din computer. Alle disse skridt er også beskrevet i GitHub's egen dokumentaiton som du kan finde her [https://docs.github.com/en/desktop](https://docs.github.com/en/desktop).

## Sæt lokal kube og branch op.
Man må ikke lave ændringer direkte i produktion eller udvikling. Hvis man ønsker at ændre noget skal det ske ved at man laver ændringerne i en privat kube, og herefter "pusher" og "merger" det med udvikling og produktion via. GutHub.
For at lave ændringer i en lokal kube skal man gøre følgende:
- På vores analysis server i udvikling har vi nogle ekstra kuber. Her kan man få sin egen kube og omdøbe den til noget som giver mening f.eks. "ProjektVersionsstyring".
- Gå ind i GitHub Desktop og vælg repositoriet "CHRU_HRKube" og klik "newBranch".
- Kald den det samme som din private kube hedder og sig at den skal bygge på "udvikling".
- Nu skulle der gerne stå "Current Branch: "ProjektVersionsstyring" i toppen.
- Ved at højreklikke på "Current Repository" kan du let finde den mappe hvor repositoriet er.

## Deploy 
Du kan nu deploye den tabulare model til din private kube, lave ændringer på den og gemme dem på din nye branch. Dette gøres på følgende måde:
- 

