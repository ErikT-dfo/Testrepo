# Beskrivelse RPA prosess

  ----------------------------------------------------------------------------
  **Prosessansvarlig**   Irene? Men har hatt mye kontakt med Ingebjørg Austbø
  ---------------------- -----------------------------------------------------
  **Seksjon/Avdeling**   REISE

  **Sak**                19726

  **Ansvarlig (RPA)**    Christina Slåttli (Nimah Elmi)

  **Kjører**             Manuell start i supportpakker og ved nye satser
                         (reise har kontroll)

  **Tidskritisk ja/nei** ja

  **Kunder**             Nei, TOA 499

  **Restartes ja/nei**   Ja, men husk å kjør prosess først:
                         DFO_Supportpakke_Delete_Travel_Testing

  **Støtter "Stop"**     Nei, Skal ikke brukes
  ----------------------------------------------------------------------------

Dette dokumente inneholder ikke dokumentasjon. Men informasjon om hvor
dokumentasjon kan finnes.

# Før prosessen skal kjøres: 

-   Reise må oppdatere testcaser i excelark

-   RPA utvikler må laste opp nye testcaser og publisere det til
    orchestrator

-   Reise har ansvar for å sette nye passord til testbrukere. Foreløpig
    har RPA utvikler oppdatert det i orchestrator, her:

![Et bilde som inneholder tekst, programvare, skjermbilde Automatisk
generert
beskrivelse](images/image1.png){width="6.3in"
height="1.2833333333333334in"}

# Fellesområdet

Fellesområdet: F:\\LA\\06 LA FF\\02 Prosesser\\10 RPA\\DFO supportpakke

Her ligger:

-   Testresultatet for hvert regulativ i et excelark

-   Alle PDFer for reiseregning (i egen mappe)

![Et bilde som inneholder tekst, Font, skjermbilde, line Automatisk
generert
beskrivelse](images/image2.png){width="3.3665912073490816in"
height="1.0991896325459318in"}

-   Hvis et testcase feiler, legges det bilder inn i mappen
    «exceptionScreenshot».

![Et bilde som inneholder tekst, skjermbilde, Font, line Automatisk
generert
beskrivelse](images/image3.png){width="3.4892760279965005in"
height="0.8050109361329834in"}

# Sharepoint

Link:
<https://dirfo.sharepoint.com/sites/net-rpa/Shared%20Documents/Forms/AllItems.aspx?csf=1&web=1&e=umgKIj&cid=35a6a7f6%2D4b21%2D42bc%2Da6e7%2Dd1b455935f62&RootFolder=%2Fsites%2Fnet%2Drpa%2FShared%20Documents%2FRPA%20LD%2FTest%20Suite&FolderCTID=0x01200016E09B05BA92B74CB10D4575466063F4>

Viktige dokumenter her i sharepoint:

-   Reise må oppdatere testcaser innimellom. Det lastes opp i filen
    «Kopi av Testcase»

![Et bilde som inneholder tekst, Font, nummer, line Automatisk generert
beskrivelse](images/image4.png){width="3.024663167104112in"
height="0.6801487314085739in"}

Inne i mappen documentation ligger det forskjellig dokumentasjon som er
viktig for REISE og for RPA utvikler.

-   Det dokumentet jeg bruker mest er «How to update testcases in DFO
    supportpakke». Jeg husker aldri hvordan dette gjøres, men følger
    oppskriften i doukmentet, og det fungerer.

-   For å skaffe seg en oversikt over prosessen kan det være lurt å lese
    igjennom «Veiledning til seksjon Reise - automatisert testing». Her
    forklares det hvordan prosessen fungerer og hvordan den hånteres fra
    orchestrator. REISE har ikke kontroll over hvordan prosessen
    startes, så det må RPA teamet gjøre for de.

![Et bilde som inneholder tekst, nummer, programvare, Font Automatisk
generert
beskrivelse](images/image5.png){width="6.3in"
height="2.3465277777777778in"}

# Prosess: DFO_Supportpakke_Delete_Travel_Testing

En person kan ikke ha flere reiser på samme tidspunkt. Når siste
testcase er kjørt i et regulativ starter prosessen automatisk slik at
det ikke skal oppstå feilmelding i portalen: «Det finnes allerede
reisedata i tidsrommet».

Det kan være greit å vite om denne prosessen. Den startes ofte manuelt
når RPA utvikler tester, hvis ikke kan testcaser feile unødvendig.

# Prosess: TemplatesAutomatedTesting

Prosessen er bygget på en lik måte at den bruker noe som heter Object
reposetory. Dette er et «bibliotek» med alle aktivitene (click/set text
osv) som benyttes i DFO_Suppportpakke.

![Et bilde som inneholder tekst, skjermbilde, programvare,
Multimedieprogramvare Automatisk generert
beskrivelse](images/image6.png){width="1.6875in"
height="1.2965277777777777in"}Hvis en aktivitet må oppdateres i
DFO_Supportpakke, så kan det enten gjøres i prosessen
TemplatesAutomatedTesting, eller direkte inn i prosessen. Anbefales at
dette gjøres i templates.

Åpne Object reposetory, gjør endringen på eksisterende aktivitet.
Eventuelt lag nye aktiviteter ved å velge «Capture Elements».

![Et bilde som inneholder tekst, skjermbilde, programvare,
Multimedieprogramvare Automatisk generert
beskrivelse](images/image7.png){width="3.6173425196850393in"
height="3.813520341207349in"}

Publiser prosessen til orchestrator, så sjekk inn til TFS. Gå på manage
packages i DFO_Supportpakke, og last ned nyeste pakke av
TempelatesAutomatedTesting. Da er endringen tilgjengelig i object
Reposetory tilgjengelig og man kan drag and drop inn nye aktiviteter. NB
Alle packages må ha samme versjon i templates og i hovedprosessen.
