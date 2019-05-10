## Notater fra møtet

### Hvordan finner man ut om et sikkerhetshull har blitt utnyttet?

  - Et forslag var at man kunne sjekke i
    VG[1](http://www.vg.no/teknologi/artikkel.php?artid=562816) :-)
  - Søke på google etter kjente utnyttede feil på egne sider
  - Passe på å logge informasjon på ulike nivåer.
  - Sjekke logger (web, app, database).
  - Sjekke data i database.
  - Sjekke oversiktssider med informasjon om nettsteder som er
    utnyttet/utnyttbare:
    zone-h/xssed.com/google-serversidefeilmeldingssøking/
  - Benytte IDS for å overvåke trafikk til og fra nettstedet.
  - Ta sjekksummer (MD5, SHA-256 el) av viktige komponenter (filer,
    databaseobjeker etc) når systemet har "kjent sikker tilstand" og
    jevnlig sjekke nåtilstand opp mot referansesjekksummen.

### Er det noen forebyggende ting man kan gjøre slik at man lettere kan finne ut om sårbarheter blir utnyttet?

  - Sjekksummer av filer/objekter i database når man har "kjent sikker
    tilstand"
  - Lage applikasjonsnær-IPS/IDS... Vær forsiktig... Mye jobb. Vanskelig
    å få treffsikkert.

### Når i utviklingsprosjektet bør sikkerheten i analyseres/testes?

  - ofte
  - viktig at det er ressurser til å ta tak i de feilene som oppdages
  - ved viktige endringer bør det gjøres en sikkerhetsvurdering
  - MS-sdlc for smidig utvikling (trusselmodellering på all ny
    funksjonalitet + fuzzing av filgrensenitt sjeldnerer)
  - sikkerhet i smidig-prosjekter (affi syntes å huske en presentasjon )
  - Dave Wichers:
    <http://video.google.com/videoplay?docid=-8287209466278543377>

### Hvordan kan man som tredjepart gi råd om hvilke sårbarheter som må fjernes før applikasjonen settes i produksjon?

  - sette krav på forhånd. Da er det lett å håndtere funn i etterkant.
  - klassifisere utnyttbarheten til sårbarheter
      - lett - kan utnyttes direkte fra nettleseren
      - vanskelig - kan bare gjøres med ekstra verktøy (plugins,
        standalone proxy...)

### Kan automatiske verktøy for sikkerhetssjekking brukes som en del av f.eks. CI?

  - ja, men viktig at informasjonen tas tak i og ikke bare blir
    "arkivert"
  - Selenium - <http://seleniumhq.org/>
  - Watir - <http://wtr.rubyforge.org/>
  - cucumber - (business driven development test verktøy)
    <http://cukes.info/>
  - MS har noen verktøy i siste versjon av Visual Studio
  - OWASP Testing guide har en oversikt over verktøy...