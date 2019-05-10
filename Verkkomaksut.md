**Ohjeet turvallisen verkkomaksuintegraation tekemiseen**

Tämä lista on tarkoitettu muistilistaksi kehittäjille, jotka toteuttavat
suomalaisten pankkien verkkomaksu-integraatioita. Listassa on nostettu
esiin asioita, jotka on tärkeä huomioida kehitystyössä. Eri pankkien
määritelmät poikkeavat toisistaan monelta osin, ja pankkikohtaisten
erojen ottaminen huomioon kehitystyössä on tärkeää. Tämä lista kattaa
yleisellä tasolla tyypillisiä verkkomaksuihin littyviä huomionarvoisia
asioita, mutta se ei ole kattava lista turvallisen
verkkomaksuintegraation toteuttamiseen. Kokonaisvaltaisesti turvallisen
verkkokaupan toteuttamiseen on tarjolla paljon materiaalia muualla tällä
sivustolla. [1](http://www.owasp.org/index.php/Category:OWASP_Project)

## 1\. Varmista pankin paluutietojen oikeellisuus

Varmista, että kaikissa "OK"-paluuosoitteissa tulevat paluutiedot
tarkistetaan oikein käyttäen mukana tulevaa tarkistetta ja kaikkia
tarvittavia tietokenttiä. Pankin laskeman tarkisteen vertaamisen lisäksi
tulee varmistaa myös, että paluutiedot liittyvät juuri oikeaan
ostotapahtumaan, mikäli paluuosoitteessa on viittaus siihen.

*Huomioitavaa:* Esimerkiksi Nordea-pankissa paluutiedot lasketaan myös
CANCEL ja REJECT url:issa ilman RETURN_PAID-kenttää, eli pelkkä oikean
tarkisteen olemassaolo ei riitä osoittamaan maksun onnistumista.
Onnistuneessa maksussa tulee olla RETURN_PAID kenttä mukana. Jos sitä
ei ole, ei maksu ole onnistunut. Eri pankkien määritelmät poikkeavat
toisistaan myös muilla tavoin, mikä tulee ottaa huomioon toteutuksessa.

## 2\. Varmista maksutapahtumien kertakäyttöisyys

Varmista, että maksun viitenumero/arkistointitunnus säilytetään.
Maksutapahtumia hyväksyttäessä tulee tarkastaa, ettei vastaanotettua
viitenumeroa/arkistointitunnusta ole käytetty aikaisemmin.

Toistohyökkäys voi olla mahdollinen, jos verkkomaksujen viitenumeroista
tai arkistointitunnuksista ei pidetä kirjaa eikä tarkasteta.

## 3\. Varmista maksun onnistuminen pankista transaktion jälkeen

Suurien ostosten yhteydessä on suositeltavaa aina tarkastaa tililtä,
että maksu on todellisuudessa saapunut perille, ennen kuin tuote
lähetetään asiakkaalle.

Mikäli tarkisteavaimet ovat päätyneet vääriin käsiin, on hyökkääjällä
mahdollisuus luoda väärennettyjä maksuja. On suositeltavaa tehdä
maksukysely jokaisen onnistuneen paluuviestin jälkeen, eikä luottaa
pelkkään paluuviestiin.

## 4\. Säilytä tarkisteavaimet turvallisesti

Tuntemalla tarkisteavaimet on mahdollista väärentää maksutapahtumia,
minkä vuoksi pääsy niihin tulee rajata mahdollisimman harvoille.

Tarkisteavaimet tulee siirtää suojattuun sijaintiin siten, että:

  - ne eivät ole web-root tai sen alla olevassa hakemistossa
  - tiedostojärjestelmätason oikeudet tarkisteavaimiin on rajattu
  - tiedosto on salattu tai sijaitsee salatussa levyosiossa (vaatii
    salasanan palvelimen käynnistyessä)

Suositeltavaa on tehdä tarkisteavaimien käsittely täysin eriytetyssä
ympäristössä erillään varsinaiselta verkkokauppapalvelimelta. Tämä
rajoittaa pääsyä tarkisteavaimiin sekä oman henkilöstön, että
mahdollisen hyökkääjän taholta.

## 5\. Määritä prosessi tarkisteavaimien vaihtamiselle

Suunnittele prosessi, kuinka käytännössä vaihdetaan tarkisteavaimet
niiden joutuessa vääriin käsiin tai avainhenkilöstön vaihtuessa.

## 6\. Määritä paluuosoitteet käyttäen ainoastaan salattua yhteyttä

Varmista lähdekoodista, että kaikki paluuosoitteet alkavat
https-alkuisella osoitteella, jolloin pankin tekemä uudelleenohjaus ei
välity salaamattomana. Jos verkkokauppatoteutus tekee itse
uudelleenohjauksen salattuun osoitteeseen vasta verkkokaupan päässä,
tieto kulkee verkossa ensin salaamattomana.

## Linkkejä eri pankkien verkkomaksujen palvelukuvauksiin

**Nordea**
[2](http://www.nordea.fi/sitemod/upload/root/fi_org/appx/fin/yri/pdf/E_maksu.pdf)

**Aktia / SP / POP**
[3](http://www.samlink.fi/verkkomaksu/pdf/Sp_Pop-k%C3%A4ytt%C3%B6ohje_fi_v1.5_152010.pdf)

**Handelsbanken**
[4](http://www.handelsbanken.fi/shb/inet/istartfi.nsf/FrameSet?OpenView&iddef=&navid=10_Verkkopalvelut&sa=/Shb/Inet/ICentFi.nsf/Default/qBAEB284F1A14043EC2257149003829DB)

**Osuuspankki** [5](https://www.op.fi/op?cid=150373005&srcpl=4)

**Tapiola**
[6](http://www.tapiola.fi/NR/rdonlyres/117DC3E2-E5AB-4179-B0FD-4DD62FB96BEA/0/Verkkomaksunpalvelukuvaus.pdf)

**S-pankki**
[7](http://www.s-pankki.fi/palvelut_yrityksille/verkkomaksu/fi_FI/verkkomaksu/_files/81046607223128605/default/Verkkomaksun%20palvelukuvaus%2012_2009.pdf)

**Sampo pankki**
[8](http://www.sampopankki.fi/fi-fi/Yritysasiakkaat/Keskisuuri-yritys/Verkkopalvelut/Documents/Sampo%20Pankin%20verkkomaksupalvelu.pdf)

**Ålandsbanken** ?

## Linkkejä muiden toimijoiden palvelukuvauksiin

**Verkkomaksut**
[9](http://www.verkkomaksut.fi/files/fi_svm_rajapintakuvaus.pdf)

**Luottokunta DMP** (vaatii rekisteröitymisen)
[10](http://www.luottokunta.fi/fi/vastaanottopalvelut/verkko_ja_muu_etakauppa/digitaalinen_maksupalvelu)