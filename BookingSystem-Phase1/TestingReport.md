1. Johdanto:
- Tehtävän tarkoituksena oli tarkastella BookingSystem palvelun kirjautumissivustoa ja siihen liittyviä tietoturvariskejä. Tarkastelussa oli ainoastaan /register polun sisältämät ongelmat.
- Testaus tapahtui 14.2-20.2 välisenä aikana. Testaus suoritettiin paikallisesti KaliOS virtuaalikoneella ja testauksien apuna käytettiin ZAP- työkalua. HUD- methodia tässä tapauksessa.

1. Yhteenveto:
- Keskeiset löydökset-
	- Salasanat eivät olleet cryptattyja. Tämä johtaa siihen, että käyttäjien tilit eivät ole turvattuja. Tämän korjaus on ehdoton ohjelmiston tulevaisuuden kannalta.
	- Path Traversal- hyökkäys(Hakemistohaku) on sivustolla mahdollinen. Hyökkääjä voi käyttää tietopolkuja, jotka eivät ole tarkoitettu heille ja täten päästä käsiksi tietoihin jotka ovat Web-juuren ulkopuiolelle
	- SQL-injektio. "Username" parametrille voidaan pakkosyöttää SQL komentoja, jolloin hyökkääjä pääsee käsittelemään tietokantoja.
- Yleinen arvio tietoturvan tilasta.
	- Tietoturva on lähes olematonta. Ongelmia on useita ja monet niistä vaatii välitöntä huomiota.
2. Löydökset ja löydöksien kategoriointi:

- Yksityiskohtainen kuvaus ja kategoriointi löydetyistä poikkeamista ja haavoittuvuuksista

<span style="color:red">
Path Traversal - Riskiluokka: High - 3 Kpl 
 </span>
 - Kuten mainittu polkujen hyväksi käyttö päästäkseen käsiksi tietoihin joihin ei ole asiaa.
 <span style="color:red">
SQL Injection - Riskiluokka: High - 4 kpl
</span>
 - Pakotettu SQL komennon syöttäminen, jotta päästään tietokantoihin käsiksi
<span style="color:yellow">
Content Security Policy (CSP) Header Not Set - Riskiluokka: Medium - 1 kpl
</span>
- Ei ole rajoitettu mistä sivusto saa ladata resursseja. Tämä voi johtaa mm: ulkoisen koodin syöttämisen palveluun
<span style="color:yellow">
Format String Error - Riskiluokka: Medium - 1 kpl
</span>
 - Ohjelma saattaa lukea käyttäjän syöttämää teksiä formaattikomentona sen sijaan, että se käsittelisi sitä pelkkänä tekstinä .
 <span style="color:yellow">
Missing Anti-clickjacking Header - Riskiluokka: Medium - 1 kpl
</span>
- Sivustoa ei ole suojattu "ClickJacking"- hyökkäykseltä, josta voi seurata tietojan kaappaaminen
<span style="color:green">
X-Content-Type-Options Header Missing - Riskiluokka: Low - 3 kpl
</span>
- Otsikolle ei ole annettu "NoSniff" arvoa, jonka seurauksena selaimet voivat tulkita tietoa väärin ja täten käsitellä sitä väärin
<span style="color:blue">
User Agent Fuzzer - Riskiluokka: Informational -  12 kpl
</span>
- Ohjelman vaste voi riippua siitä, millainen selain tai hakukone on käsittelemässä tietoa.
[ZAP-report](zap-report.md)
