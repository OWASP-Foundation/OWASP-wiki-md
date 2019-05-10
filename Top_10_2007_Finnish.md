## Johdanto

**Huom\! Tätä sivua työstetään edelleen. Tältä sivulta linkittyvien
alasivujen suomennostyöhön saa osallistua kuka tahansa.**

Tervetuloa OWASP Top 10 2007 -dokumentin suomennettuun versioon\! Top 10
2007 kuvaa kymmentä tyypillisintä nykyään käytettävistä
web-sovelluksista havaittua haavoittuvuutta. Dokumentti on
uudelleenkirjoitettu alkuperäisestä vuoden 2004 versiosta.

Java Enterprise Edition -kohtainen lista dokumentista on ladattavissa
[täältä](https://www.owasp.org/images/8/89/OWASP_Top_10_2007_for_JEE.pdf).

## Tavoitteet

**OWASP Top 10:n tärkein tavoite on kouluttaa sovelluskehittäjiä,
suunnittelijoita, arkkitehtejä ja organisaatioita** tyypillisimpien
sovellushaavoittuvuuksien seurauksista. Top 10 tarjoaa perusmenetelmät
näiltä haavoittuvuuksilta suojautumiseen - loistava ensiaskel
turvalliseen ohjelmistokehitykseen.

**Tietoturvallisuutta ei saavuteta kerralla**. Ei riitä, että sovellus
tehdään turvalliseksi kerran. Esimerkiksi nyt lukemasi lista on
muuttunut vuosien varrella, ja sovelluksen lähdekoodin käsittely uusien
uhkien valossa takaa sovelluksen turvallisuuden jatkossakin. Lisätietoja
ja tarkempia suosituksia on tarjolla englanninkielisessä dokumentissa
[Where to Go From Here](Top_10_2007-Where_to_Go_From_Here "wikilink").

**Turvallisen ohjelmoinnin periaatteita tulee noudattaa läpi koko
sovelluksen elinkaaren.** Turvallinen web-sovellus on mahdollinen
***vain*** kun turvallisen ohjelmistokehityksen elinkaarimalli (Secure
SDLC - Software Development Life Cycle) on mukana. Tämän mallin tulee
olla oletuksena mukana sekä suunnitteluvaiheessa että kaikissa
kehitysvaiheissa. Kaiken kaikkiaan erilaisia web-sovellusten
tietoturvallisuuteen vaikuttavia tekijöitä voidaan nimetä yli 300.
Näistä tekijöistä on tarkempia kuvauksia englanninkielisessä
dokumentissa [OWASP Development Guide](OWASP_Guide_Project "wikilink"),
joka sisältää oleellista luettavaa kaikille web-sovelluskehittäjille.

**Tämän dokumentin ensisijainen tarkoitus on olla opetuksellinen, ei
standardi**. Älä käytä tätä dokumenttia tietoturvallisuuden ohjenuorana
tai standardina ottamatta [meihin yhteyttä](mailto:owasp@owasp.org)
ensin\! Jos tarvitset turvallisen ohjelmistokehityksen standardia,
OWASPilla on käynnissä tähän liittyviä muita projekteja. Liittymällä
mukaan tai antamalla tukea näihin projekteihin tuet niiden edistymistä
parhaiten.

## Kiitokset avustajille

|                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OWASP Foundation kiittää [MITREä](http://www.mitre.org/) CVE-tietokannan *Vulnerability Type Distribution -osion* [tietojen](http://cve.mitre.org/docs/vuln-trends/index.html) saattamisesta yleiseen käyttöön. Kansainvälistä OWASP Top Ten -projektia vetää ja sen sponsorina toimii [<https://www.owasp.org/images/d/d1/Aspect_logo.gif>](http://www.aspectsecurity.com). |

Projektipäällikkö: Andrew van der Stock (Executive Director, OWASP
Foundation)

Työryhmä: Jeff Williams (Chair, OWASP Foundation), Dave Wichers
(Conference Chair, OWASP Foundation)

OWASP Foundation kiittää osaltaan seuraavia avustajia ja kommentoijia:

  - Raoul Endres (hankkeen kommentointi)
  - \[[mailto:coley](mailto:coley)...at...mitre.org Steve Christey\]
    (MITRE) (aineiston perinpohjainen vertaisarviointi, MITRE CWE -datan
    lisääminen)
  - Sylvan von Stuppe (aineiston perinpohjainen vertaisarviointi)
  - [Jeremiah Grossman](http://jeremiahgrossman.blogspot.com/)
    ([WhiteHat Security](http://www.whitehatsec.com/)) aineiston
    arviointi, automaattisten havaintomenetelmien arviointi
  - [Neil Smithline](http://www.smithline.net/)
    ([OneStopAppSecurity.com](http://www.OneStopAppSecurity.com/))
    (kommentit ja Wiki-version luonti)
  - Colin Wong, Nigel Evans, Andre Gironda (sähköpostikommentointi)

Dokumentin käännöstyöhön Suomessa ovat osallistuneet [OWASP Helsinki
-jaoksen](http://www.owasp.org/index.php/Helsinki) aktiivijäsenet.

## Kooste

|                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [A1 - Verkkosivun rakenne ei säily (XSS)](Top_10_2007-A1-Finnish "wikilink")                   | Sovellus on haavoittuva verkkosivun rakenteen muutoshyökkäykselle (XSS), kun se välittää käyttäjän antaman syötteen selaimelle sellaisenaan tarkistamatta ja käsittelemättä sitä ensin asianmukaisesti. Tämä mahdollistaa hyökkääjältä tulevien komentojen suorittamisen sovelluksen alaisuudessa. Komennoilla voidaan muuttaa selaimessa esimerkiksi sivuston ulkoasua tai kaapata sivuston istuntotunnisteet.                                                                                  |
| [A2 - Taustajärjestelmäkyselyn rakenne ei säily](Top_10_2007-A2-Finnish "wikilink")            | Taustajärjestelmäkyselyn rakenteen muutoshyökkäykset, erityisesti SQL-tietokantakyselyn rakenteen muutoshyökkäys (SQL-injektio), ovat tyypillisiä web-sovelluksiin kohdistuvia hyökkäysmenetelmiä. Kyselyn rakenteen muutos onnistuu, kun puutteellisen suodatuksen takia käyttäjän antama syöte istutetaan suoraan osaksi taustajärjestelmäkomentoa tai tietokantakyselyä. Tämä mahdollistaa hyökkääjälle komentojen ajamisen tai tiedon muuttamisen taustajärjestelmässä.                      |
| [A3 - Haitallisen tiedoston suoritus](Top_10_2007-A3-Finnish "wikilink")                       | Käyttäjän antama tiedosto tai tiedostonimi välitetään sovellukselle tarkistamatta tiedoston sisällön tai tiedostonimen oikeellisuutta. Tämä mahdollistaa hyökkääjälle tavan liittää sovelluksen käyttöön haitallista koodia tai haitallisia tiedostoja, jotka suoritetaan palvelimella.                                                                                                                                                                                                          |
| [A4 - Turvaton suora viittaus tietoalkioon](Top_10_2007-A4-Finnish "wikilink")                 | Jos sovellus käyttää suoria viittauksia sovelluksen sisäisesti käyttämiin tietoalkioihin, kuten tiedostoihin tai tietokantataulujen perusavaimiin, viittaukset voivat paljastua käyttäjälle esimerkiksi osoitekentässä näkyvien parametrien arvona. Tämä mahdollistaa hyökkääjälle pääsyn valtuuttamattomiin tietoalkioihin, esimerkiksi toisten käyttäjien salaisiin tietoihin, mikäli käytettyjen viittauksien vaihtamista toiseen ei ole estetty asianmukaisilla valtuutusten tarkistuksilla. |
| [A5 - Puutteellinen pyynnön alkuperän tarkistus (CSRF)](Top_10_2007-A5-Finnish "wikilink")     | Pyyntöhuijauksessa hyökkääjä lähettää sovellukseen kirjautuneelle käyttäjälle esimerkiksi sähköpostissa väärennetyn linkin, joka ohjaa käyttäjän selaimen suorittamaan hyökkääjän määräämän toiminnon käyttäjän valtuuksilla. Tämä voidaan tehdä täysin käyttäjän tietämättä, sillä kyseinen kutsu voidaan piilottaa esimerkiksi kuvaelementin sisään jollakin toisella sivustolla.                                                                                                              |
| [A6 - Tiedon vuotaminen ja puutteellinen virheenkäsittely](Top_10_2007-A6-Finnish "wikilink")  | Sovellukset voivat tarkoituksettomasti vuotaa tietoja omista asetuksistaan ja sisäisistä toteutustavoistaan tai jopa loukata yksityisyydensuojaa erilaisten hallitsemattomien virhetilanteiden johdosta. Hyökkääjät voivat käyttää sovelluksen virheviesteistä paljastuvia tietoja joko suoraan tai apuna suunnitellessaan vakavampia hyökkäyksiä.                                                                                                                                               |
| [A7 - Puutteellinen tunnistusmenettely ja istunnonhallinta](Top_10_2007-A7-Finnish "wikilink") | Käyttäjä- ja istuntotunnisteita ei usein ole suojattu riittävillä keinoilla. Tämä mahdollistaa hyökkääjille salasanojen sekä käyttäjä- tai istuntotunnisteiden keruun järjestelmästä. Tätä kautta sovelluksen käyttämisen toisten valtuuksilla mahdollistuu.                                                                                                                                                                                                                                     |
| [A8 - Puutteellinen tietojen salaus](Top_10_2007-A8-Finnish "wikilink")                        | Web-sovelluksissa käytetään vain harvoin asianmukaisia salausmenetelmiä tiedon ja käyttäjätunnisteiden salaukseen esimerkiksi tietokannassa. Hyökkääjä voi tällöin helposti selvittää esimerkiksi käyttäjien henkilökohtaisia tietoja ja luottokorttinumeroita päästyään tietokantaan käsiksi esimerkiksi tietokantakyselyn rakennemuutos -hyökkäyksen avulla.                                                                                                                                   |
| [A9 - Turvattomat tietoliikenneyhteydet](Top_10_2007-A9-Finnish "wikilink")                    | Sovellukset käyttävät harvoin asianmukaisesti salattuja tietoliikenneyhteyksiä. Tämä voi mahdollistaa esimerkiksi liikenteen salakuuntelun.                                                                                                                                                                                                                                                                                                                                                      |
| [A10 - Rajoittamaton URL-tason pääsy](Top_10_2007-A10-Finnish "wikilink")                      | Sovellusten pääsynvalvonta perustuu usein siihen, että valtuuttamattomalle käyttäjälle ei näytetä linkkejä niihin toimintoihin, joihin hänellä ei ole oikeuksia. Nämä osoitteet saattavat kuitenkin olla yleisesti tunnettuja tai helposti arvattavia, ja hyökkääjä pystyy suorittamaan valtuuttamattomia toimia yksinkertaisesti siirtymällä näihin osoitteisiin.                                                                                                                               |

'''

<center>

Taulukko 1: Web-sovellusten Top 10 -haavoittuvuudet 2007

</center>

'''

Tämä dokumentti sisältää myös muutamia sivuja, jotka eivät suoraan koske
mitään tiettyä haavoittuvuutta. Nämä on listattu seuraavassa taulukossa.

|                                                                                                   |                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Top 10 2007 Finnish](Top_10_2007_Finnish "wikilink")                                             | Dokumentin pääsivu (tämä sivu) tarjoaa johdannon ja mahdollisuuden lisätä kirjanmerkkeihin koosteosuuden jatkokäyttöä varten. (lisää [tämä linkki](https://www.owasp.org/index.php/Top_10_2007_Finnish#Kooste) selaimesi kirjanmerkkeihin) |
| [Top 10 2007-Methodology-Finnish](Top_10_2007-Methodology-Finnish "wikilink")                     | Kuvaus tähän dokumenttiin valittujen haavoittuvuuksien valintamenetelmistä.                                                                                                                                                                |
| [Top 10 2007-Where to Go From Here-Finnish](Top_10_2007-Where_to_Go_From_Here-Finnish "wikilink") | Vinkkejä siihen kuinka jatkaa tämän dokumentin lukemisen jälkeen.                                                                                                                                                                          |
| [Top 10 2007-References-Finnish](Top_10_2007-References-Finnish "wikilink")                       | Suositeltavaa luettavaa.                                                                                                                                                                                                                   |

'''

<center>

Taulukko 1a: Sivut *OWASP Top Ten 2007* -dokumentissa, jotka eivät liity
yllä oleviin haavoittuvuussivuihin.

</center>

'''

## Eri versioihin liittyvä huomautus

Vaikka ainut virallinen versio *OWASP Top Ten 2007* -listasta on
englanninkielinen ladattava PDF-versio, OWASP on julkaissut tämän
Wiki-sivun, joka sisältää PDF-dokumentin kanssa yhtenevät tiedot.
Toivomme että vapaaehtoispanoksesi myötä tilanne voisi muuttua ja
Wiki-versio voisi edelleen kehittyä. Tämän helpottamiseksi olemme
julkaisseet englanninkielisen
[ohjesivun](Editing:Top_10_2007 "wikilink").

## Ladattavat tiedostot

Valmiita Top 10 -dokumentteja on ladattavissa seuraavilla kielillä:

  - [(englanti, PDF 930
    kb)](http://www.owasp.org/images/e/e8/OWASP_Top_10_2007.pdf)

<!-- end list -->

  - [(ranska, PDF 455
    kt)](https://www.owasp.org/images/c/ce/OWASP_Top_10_2007_-_French.pdf)

<!-- end list -->

  - [(korea, PDF 768
    kt)](http://www.metasecurity.org/owasp/OWASP_Top_10_2007_Korean.pdf)

<!-- end list -->

  - [(turkki, PDF 718
    kb)](http://csirt.ulakbim.gov.tr/dokumanlar/Ceviri_OWASP_ilk10_2007.pdf)

<!-- end list -->

  - [(brasilianportugali, PDF 329
    kt)](http://www.owasp.org/images/4/42/OWASP_TOP_10_2007_PT-BR.pdf)

<!-- end list -->

  - [(espanja, PDF 488
    kt)](https://www.owasp.org/images/a/ae/OWASP_Top_10_2007_Spanish.pdf)

<!-- end list -->

  - [OWASP Top 10 (Java Enterprise Edition), PDF 630
    kt)](https://www.owasp.org/images/8/89/OWASP_Top_10_2007_for_JEE.pdf)

<!-- end list -->

  - Etsitkö jollain muulla kielellä laadittua versiota? Otamme
    mielellämme vastaan panoksesi käännöstyöhön. Ota yhteyttä Andrew
    van der Stockiin (vanderaj ...(@)... owasp.org) lisätietojen
    saamiseksi.