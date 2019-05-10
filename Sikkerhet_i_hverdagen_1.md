Dette er spørsmål til, og diskusjonen som fulgte på, Medlemsmøte onsdag
25. februar:

## Oppe til diskusjon

### Hva kan jeg som utvikler gjøre for å øke fokuset på sikkerhet i prosjektet?

Stilt av: Knut Vidar Siem

  - Må man spørre om å få sikre kode? Man kan definere det som en del av
    oppgaven slik som ofte gjøres med testing. Man bør imidlertid ha
    fått én eller annen form for mandat.
  - Awareness/skremsel, men ikke exploit hull i prod\!
  - Vise sparte penger/risikopenger til en lederperson
  - Sidestille sikkerhet med funksjonalitet: sikkerhetskrav
  - Gå gjennom Top 10, ikke bare nevne dem
  - Sette opp verktøy som FindBugs og diskutere funn
  - Vise at god praksis hjelper
  - Komme igang. Start i det små.

### Hvordan kan jeg som utvikler sikre 'midt i applikasjonen'-kode?

Stilt av: Knut Vidar Siem

Spørsmålet stilles altså ikke i kontekst av skjemainput eller
databasespørringer, men den store massen av helt ordinær businesskode.

  - Gjør code reviews (også) av forretningslogikk
  - Pass opp for logging av bad data med sårbar klient
  - Utvikle med fokus på kontrakter.
  - Identifiser tillitsgrensene
  - Ha et tjenestelag
  - Hvem får tilgang til å utføre ting?
  - Pass opp for skrivefeil i adgangstabellene
  - Don't do it yourself: kryptering, authn/authz, datoaritmetikk etc.
  - Bruk sterk typing der man kan
  - Cross-cutting-ting auth, cache
  - Vær eksplisitt med hva som eksponeres av modellen til browsere
  - Reduser mengden tolket kode

### Hvordan takle CSRF i Ajax-applikasjoner?

Stilt av: Kåre Presttun

  - Er svaret token frem og tilbake?
  - Hva med flere tokens "ute" samtidig i en applikasjon med mange
    forms?
  - Hvorfor sesjonsnøkler???

### Hvordan ser det generelle trusselbildet ut for Ajax?

Stilt av: ?

  - text/plain for å hindre evaluering
  - HTML 5 og klientside SQL-injection
  - Callbacks
  - Avanserte datastrukturer
  - Ufullstendig sårbarhetsscan

### Hva skal man gjøre om man oppdager et sikkerhetshull som har havnet i produksjon?

Stilt av: Baard H. Rehn Johansen

  - Patche best mulig, \*raskest\* mulig med mulighet for overvåkning
  - App.firewall med spesiell signatur kan forhindre exploits
  - mod_security kan skrive om requests til sårbare ressurser
  - Concurrency-issues gjør det hele vanskeligere
  - OWASP-prosjektet har dekket en stor mengde hull i Webgoat med
    mod_security
  - Må ha en planlagt respons på slike hendelser
  - Ta vare på beviser (rullende filer) -- ikke shutdown

### Hvordan leder man et sikkerhetsprogram i en bedrift ?

Stilt av: ?

  - Standarder ISO-27000
    [1](http://en.wikipedia.org/wiki/ISO/IEC_27000-series) (ikke så mye
    prosess; mer "hva?")
  - Noen offentlige forespørsler etterlyser 27001-sertifisering
  - COBIT [2](http://en.wikipedia.org/wiki/COBIT) går mer inn på
    "hvordan?"
  - Hvordan møtes sårbarheter og fluff?
  - Retningslinjer
  - Spesifisering og sikkerhetskrav
  - Være pragmatisk og konkret
  - Man må selv lage policies og guidelines
  - 27k1 kritiseres for å være for ekstrem i krav om målbarhet
  - Definere hva som aksepteres
  - Se på induistristandard (naboen)
  - Være aktiv og diskutere

## Ikke tatt opp

### Hvordan finner man ut om et sikkerhetshull har blitt utnyttet?

Stilt av: Baard H. Rehn Johansen

### Er det noen forebyggende ting man kan gjøre slik at man lettere kan finne ut om sårbarheter blir utnyttet?

Stilt av: Baard H. Rehn Johansen

### Hva kan vi/OWASP gjøre for bedre sikkerhet i norske utviklingsprosjekt?

Stilt av: Markus Harboe

### Når i utviklingsprosjektet bør sikkerheten i analyseres/testes?

Stilt av: Markus Harboe

### Hvordan håndterer man sårbarheter som finnes dagene før driftsetting?

Stilt av: Markus Harboe

### Hvordan håndterer man sårbarheter i applikasjoner i full drift

Stilt av: Markus Harboe (ref. Baards forsalg)

### Hvordan kan man som tredjepart gi råd om hvilke sårbarheter som *må* fjernes før applikasjonen settes i produksjon?

Stilt av: Markus Harboe

### Hvordan presentere sårbarhetsfunn for hhv. leveranse og mottakersiden?

Stilt av: Markus Harboe

### Hva finnes av verktøy for å automatisk sjekke sikkerhet?

Stilt av: Erik Drolshammer

### Kan automatiske verktøy for sikkerhetssjekking brukes som en del av f.eks. CI?

Stilt av: Erik Drolshammer