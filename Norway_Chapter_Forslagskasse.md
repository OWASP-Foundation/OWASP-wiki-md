## Hovedtema

Her kan du komme med forslag til temaer for medlemsmøtene.

  - Sårbarhetsanalyse og penetrasjonstesting
      - En gjennomgang av risikobildet slik det er nå.
  - Enterprise API, JSecurity og Spring Security (ACEGI) - presentasjon
    av rammeverkene
  - Webgoat live - kjøre live demo og evt. la deltakere forsøke selv
  - Validering av data - hvor/når/typer
  - Cross Site Scripting / SQL-injection
  - Feil i kjente rammeverk - Vise feil som har eksistert i kjente
    rammeverk
  - Hvordan få gjennomslag for økt fokus på sikkerhet?
      - Lover og regler som kan brukes i argumentasjonen. Hvilke er
        viktige i forhold til sikkerhetskrav?
      - Sikring som en naturlig del av hver utviklingsoppgave --
        utviklernes integritet
  - OWASP-guiden
  - Sikker systemutvikling i praksis - Java/.NET
  - ModSecurity sikrer din webapplikasjon (Hva er en
    applikasjonsbrannmur?)
  - Sikkerhet i hverdagen: Kan vi bli flinkere?
  - Sikring av webapplikasjoner - mer enn inputvalidering
  - Q Hva med et møte om å sikre utviklere fra seg selv. Dvs hvordan
    driftere kan sikre web løsninger i størt mulig grad.
      - A Forslag til tiltak:
          - ModSecurity (står alt på forslags listen)
          - Chroot (del av modsecurity...)
          - Apparmor/Selinux
          - Web proxy forran (stripped down Apache uten noe mer enn
            minium med moduler)
          - Kjøre apache som vanlig bruker ikke root (ikke at det noen
            gang har vært et problem..). Og når vi ønsker å kjøre den
            som root (f.eks med cgi-bin, php, ruby etc)
          - Os herding (brukeren som kjører applikasonen får ikke gjort
            noe som helst, ikke at brukeren har et shell en gang..
            noexec filsystemer etc)
          - Host iptables regler med bruker støtte. Brukeren for web
            applikasoner får ikke nådd noe annet enn de db serverene etc
            de skal nå på de rette portene...
          - Bruke SSL hele veien. Og ha serfikat uten passord. Skulle
            maskinen hackes så får de ikke endret på apache moduler etc
            uten å kjøre en start/stop. Reload/HUP leser bare config
            filene inn på nytt
          - IPS (f.eks via en host som står som "bridge mode", dvs uten
            IP og bare dropper pakker den ikke liker, forwrader alt
            annet)
          - Firewall og vlan (ikke new connections ut fra maskinene
            f.eks)
          - NAT (Billig sikkerhets sak :) )
          - Bruk av forskjellige produkter for å spre risiko (OpenBSD på
            proxy'en med lighttpd, og Linux med Apache bak som app
            servere og FreeBSD firewall)

## Tooltip

Små (10-15 min) praktiske foredrag som vi kan med hvert møte

  - Firefox som sikkerhetstestingsverktøy - Erlend Oftedal
  - Paros -
  - Burp suite -

Tilbake til [Norway](Norway "wikilink") Chapter