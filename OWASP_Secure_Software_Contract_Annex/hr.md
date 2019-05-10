Prijevod: [Tonimir
Kišasondi](https://www.owasp.org/index.php/User:Tonimir_Kisasondi),
Laboratorij za otvorene sustave i sigurnost, Fakultet organizacije i
informatike, Varaždin

### Temeljne pretpostavke:

1\. Odluke o potrebnoj razini sigurnosti temelje se na razumijevanju
rizika koji su vezani uz sustav koji se razvija.

2\. Pristup osiguravanju sigurnosti mora se temeljiti na pristupu
analize i implementacije potrebne razine sigurnosti kroz cijeli životni
ciklus proizvoda ili sustava.

3\. Kontrole tj. mjere zaštite nisu poseban, dodatni dio sustava već
integrirani dio u svim elementima sustava. Kontrole ne smiju biti
poseban ili dodatan dio razvoja sustava.

4\. Dokumentacija sustava mora sadržavati opise svih primijenjenih
kontrola u sustavu.

5\. Dokumentacija mora biti jasna, korisna i transparentna te mora
opisivati dizajn integriranog, cjelovitog sustava sigurnosti, procjenu
rizika koja je provedena u sklopu razvoja i moguće probleme.

6\. Ranjivosti u sustavu nisu neočekivane ali u procesu razvoja i u
ranim fazama životnog ciklusa sustava treba pokušati identificirati
sigurnosne manjkavosti.

7\. Informacije o sigurnosti, rizicima i ranjivostima potrebno je
otvoreno razmjenjivati između strane koja razvija sustav i koja je
korisnik sustava, čim se navedene informacije otkrije jedna strana, mora
obavijestiti drugu stranu u cijelosti i bez ustručavanja.

### Aktivnosti životnog ciklusa:

1\. Rizici moraju biti identificirani u odnosu na imovinu ili elemente
sustava, dokumentirani i obje strane moraju razumjeti rizike koji su u
kontekstu sustava.

2\. Razvoj detaljnih sigurnosnih zahtjeva za sustav mora se temeljiti na
identificiranim rizicima, gdje su sigurnosni zahtjevi dio specifikacije
sustava koji se razvija. Sigurnosne zahtjeve moguće je realizirati
dodatnim prilagođenim razvojem ili dodatnim sigurnosnim elementima u
sustavu.

3\. Svaki sigurnosni zahtjev mora biti razmotren i odluka mora biti
donesena o načinu obrade rizika. Izvođač i naručitelj sustava moraju
biti suglasni oko svih opisanih sigurnosnih zahtjeva i kontrola. Odluke
moraju dokumentirane, te dokumentacija mora sadržavati informaciju zašto
je konkretna kontrola prikladna i na koji način odgovara u cjelokupnom
sustavu uz sva njegova ograničenja. Bitno je navesti da li se kontrola
temelji na ugrađenom elementu koji je dio sustava ili je kontrola
element koji razvija treća strana. Svaki sigurnosni zahtjev mora biti
formiran na način da je moguće provjeriti da li je ispunjen.

4\. Razvoj sustava mora se temeljiti na elementima koji su sigurni i
odgovaraju zahtjevima sigurnosti.

5\. Svi elementi sustava moraju proći provjeru od druge strane koja nije
razvijala konkretni element sustava. Cijeli sustav mora odgovarati
dogovorenoj normi verifikacije mjera sigurnosti kao što je OWASP ASVS
ili nekoj drugoj. Rezultati verifikacije moraju biti dokumentirani prema
zahtjevima norme za verifikaciju.

6\. Sustav mora sadržavati opis postavki i njihove implikacije za
sigurnost sustava. Opis mora sadržavati i opis zavisnosti kao što je
potrebna inačica operacijskog sustava, web poslužitelja, sustava za
upravljanje bazom podataka i način na koji isti moraju biti podešeni da
odgovaraju zahtjevima sigurnosti cijelog sustava. Početna konfiguracija
sustava u trenutku isporuke mora biti sigurna.

### Zahtjevi sigurnosti:

Prilikom procjene rizika i definiranja sigurnosnih zahtjeva potrebno je
uzeti u obzir sljedeće zahtjeve sigurnosti koji moraju uključivati:

1\. Pravila za provjeru unosa i kodiranje svakog ulaza u aplikaciju, bez
obzira da li je unos od korisnika, baze podataka ili vanjskih sustava.
Početna pretpostavka je da su svi unosi nevaljani osim ako ne odgovaraju
specifikaciji točnog unosa. Zahtjevi moraju sadržavati postupak što
uraditi sa unosom koji nije valjan. Sustavi ne bi smjeli biti podložni
napadima umetanja znakova, prelijevanja spremnika, neovlaštenom
promjenom i ostale napade koji mijenjaju stanje sustava.

2\. Mjere kako će se štiti sesija korisnika te podatci kojima se
identificira sesija i prijavljeni korisnik. Zahtjevi moraju uključivati
mjere za sve povezane funkcije kao što su: vraćanje zaboravljene
lozinke, promjene lozinke, odjave, višestruke prijave i druge.

3\. Detaljan opis načina realizacije kontrole pristupa te uloge, grupe,
privilegije i autorizacije koje se koriste u aplikaciji vezane uz
imovinu i funkcije koje su unutar sustava, gdje se povezuju specifična
prava pristupa za svaku imovinu ili funkciju po svakoj ulozi. Predlaže
se uporaba matrice kontrole pristupa za opis uloga i razine prava
pristupa.

4\. Način ponašanja sustava prilikom greške u radu. U nekim slučajevima
najbolje je pružiti korisniku najbolji pokušaj u slučaju greške a nekada
je najbolje prekinuti izvršavanje odmah. Navedene situacije i način
baratanja greškama mora biti definiran prije izgradnje sustava.

5\. Način bilježenja događaja u sustavu kao što su uspješne i neuspješne
prijave, uočeni napadi ili pokušaji zaobilaženja autorizacije. Zahtjevi
moraju sadržavati i podatke koji se moraju bilježiti kao što je vrijeme,
datum, detalji aplikacije i sve ostale podatke koji omogućavaju
forenzičku analizu.

6\. Oblik autentikacije i zaštite komunikacije kao što je kriptiranje
komunikacije i veze sa drugim elementima sustava kao što su baze
podataka ili drugi web servisi. Vjerodajnice za uspostavu komunikacije
moraju biti također zaštićene na primjeren način.

7\. Odluku koje podatke treba kriptirati, na koji način kriptirati te
kako će se postupati sa certifikatima i vjerodajnicama. Sustav mora
koristiti standardne preporučene algoritme i biblioteke koje su
sigurnosno provjerene.

8\. Način zaštite sustava od napada uskraćenjem usluge (DoS ili DDoS), u
obzir treba uzeti razne vrste napada kao što je zaključavanje
autentikacije nakon većeg broja neuspješnih pokušaja, iscrpljivanja
broja konekcija i ostale napade iscrpljivanjem resursa.

9\. Početne vrijednosti konfiguracije moraju biti fokusirane prema
sigurnim postavkama. Sustav mora omogućiti lagani pregled svih
relevantnih opcija i postavljene vrijednosti za provjeru sigurnosti.

10\. Popis ranjivosti koje su uklonjene tijekom razvoja i kontrole koje
su postavljene.

### Osoblje i organizacija:

1\. Uz razvoj, dodatna verifikacija sigurnosti trebala bi se provoditi
kroz arhitekte sigurnosti koji razumiju problematiku razvoja sigurnih
elemenata sustava.

2\. Članovi tima za razvoj moraju biti obučeni i educirani u najboljoj
praksi izgradnje sigurnih sustava vezanih uz njihove uloge.

3\. U slučaju razvoja povjerljivih sustava treba razmotriti primjerenost
provjere sigurnosti i prijašnje iskustvo razvojnog tima uz dodatne
ugovore o povjerljivosti.

### Razvojno okruženje:

1\. Razvojni tim mora koristiti sustav za upravljanje izvornim tj.
programskim kodom sa označivanjem promjena koje je napravio koji član
razvojnog tima nad konfiguracijskim datotekama, datotekama izvornog koda
i postavkama sigurnosti.

2\. Razvojni tim mora koristiti način izgradnje softvera iz izvornog
koda koji omogućuje provjeru integriteta softvera koji je isporučen
klijentu.

### Biblioteke, okviri i proizvodi:

1\. Svi elementi sustava koji nisu razvijeni u sklopu projekta, već ih
je razvila treća strana moraju biti poznati klijentu uz navođenje da li
su komercijalni, besplatni, otvorenog koda ili zatvorenog koda.

2\. Izvođač mora uložiti razuman trud da osigura da elementi koje je
razvila treća strana odgovaraju zahtjevima sigurnosti projekta.

### Provjera sigurnosti:

1\. Klijent ima pravo provjeriti sigurnost sustava u svojem trošku u
roku 60 dana od isporuke. Razvojni tim mora omogućiti razumnu podršku
timu koji provodi provjeru sigurnosti davajući uvid u izvorni kod i
testne okoline.

2\. Provjera sigurnosti mora uključivati i pokrivati sve elemente
sustava uključujući i prilagođene elemente sustava, komponente,
proizvode i konfiguraciju.

3\. Provjera sigurnosti mora minimalno uključivati provjeru za poznatim,
čestim ranjivostima. Provjera može uključivati kombinaciju provjere
ranjivosti, penetracijskog testa, statičke analize izvornog koda i
pregled elemenata sustava od strane eksperta.

4\. Sigurnosni nedostatci koji se otkriju u sklopu provjere moraju biti
preneseni i klijentu i razvojnom timu.

### Upravljanje sigurnosnim nedostacima:

1\. Sigurnosne nedostatke treba pratiti i uklanjati kroz cijeli životni
ciklus sustava, bilo da su dio sigurnosnih zahtjeva, dizajna,
implementacije, testiranja, isporuke ili da su operativni problem. Rizik
vezan uz svaki sigurnosni nedostatak mora biti evaluiran, dokumentiran i
klijent mora biti izviješten o nedostatku i riziku čim se isti otkrije.

2\. Razvojni tim će primijeniti razumne mjere zaštite informacija veznih
us sigurnosne nedostatke i dokumentaciju o istima zbog zaštite klijenta.

3\. Svi sigurnosni nedostatci koji su pronađeni prije isporuke biti će
ispravljeni od strane razvojnog tima. Postupanje sa sigurnosnim
nedostatcima otkrivenima nakon isporuke određuje se ugovorom a isti se
smatraju kao bilo koja druga manjkavost u softveru.

### Osiguravanje kvalitete:

1\. Razvojni tim će uz dokumentaciju projekta predati i sigurnosnu
dokumentaciju koja uključuje sve sigurnosne zahtjeve, dizajn sustava
sigurnosti, implementaciju kontrola, rezultate testiranja te potvrdu da
su svi sigurnosni nedostatci uklonjeni prije isporuke softvera.

2\. Arhitekt sigurnost mora potvrditi da sustav zadovoljava zahtjeve
sigurnosti i da su sve aktivnosti u pogledu obrade rizika provedene. Sve
iznimke moraju biti dokumentirane i evidentne u isporuci i
dokumentaciji.

3\. Razvojni tim jamči da sustav nema elemenata koji oslabljuju
sigurnost a nisu dio zahtjeva klijenta kao što su virusi, crvi,
zaobilaženja autentikacije tj. “stražnja vrata”, trojanski konji i
ostali oblici malicioznog koda

### Održavanje sustava i prihvaćanje:

1\. Sustav ne može biti prihvaćen prije nego što su uklonjeni svi
sigurnosni nedostatci i rezultati provjere sigurnosti prihvaćeni od
strane klijenta.

2\. Nakon prihvaćanja sustava, ukoliko se pronađu ili se sumnja na
dodatne sigurnosne manjkavosti, Izvođač će pomoći klijentu u
istraživanju manjkavosti. Ukoliko klasa manjkavosti nije pokrivena
sigurnosnim zahtjevima i nalazi se izvan opsega sigurnosnog testiranja,
manjkavost se smatra dodatnim razvojnim zahtjevom. Takvi dodani zahtjevi
biti će obrađivani dogovorom i odlukom između izvođača i klijenta.

3\. Izvođač mora primijeniti razumne mjere, koje uključuju razvoj
sustava prema najboljim praksama koje uključuju način uklanjanja
sigurnosnih manjkavosti prema razini rizika u cilju čim prije obrade
rizika u suglasnosti sa klijentom.

__NOTOC__

[Category:OWASP Legal Project](Category:OWASP_Legal_Project "wikilink")
[Category:OWASP Secure Software Contract
Annex](Category:OWASP_Secure_Software_Contract_Annex "wikilink")