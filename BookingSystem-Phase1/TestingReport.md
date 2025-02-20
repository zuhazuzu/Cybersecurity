1. Johdanto:
- Tehtävän tarkoituksena oli tarkastella BookingSystem palvelun kirjautumissivustoa ja siihen liittyviä tietoturvariskejä. Tarkastelussa oli ainoastaan /register polun sisältämät ongelmat.
- Testaus tapahtui 14.2-20.2 välisenä aikana. Testaus suoritettiin paikallisesti KaliOS virtuaalikoneella ja testauksien apuna käytettiin ZAP- työkalua. HUD- methodia tässä tapauksessa.

2. Yhteenveto:
- Keskeiset löydökset-
	- Salasanat eivät olleet cryptattyja. Tämä johtaa siihen, että käyttäjien tilit eivät ole turvattuja. Tämän korjaus on ehdoton ohjelmiston tulevaisuuden kannalta.
	- Path Traversal- hyökkäys(Hakemistohaku) on sivustolla mahdollinen. Hyökkääjä voi käyttää tietopolkuja, jotka eivät ole tarkoitettu heille ja täten päästä käsiksi tietoihin jotka ovat Web-juuren ulkopuiolelle
	- SQL-injektio. "Username" parametrille voidaan pakkosyöttää SQL komentoja, jolloin hyökkääjä pääsee käsittelemään tietokantoja.
- Yleinen arvio tietoturvan tilasta.
	- Tietoturva on lähes olematonta. Ongelmia on useita ja monet niistä vaatii välitöntä huomiota.
3. Löydökset ja löydöksien kategoriointi:
- Yksityiskohtainen kuvaus ja kategoriointi löydetyistä poikkeamista ja haavoittuvuuksista

Path Traversal - Riskiluokka: $\color{red}{\textsf{High}}$ - 3 Kpl 
 - Kuten mainittu polkujen hyväksi käyttö päästäkseen käsiksi tietoihin joihin ei ole asiaa.

SQL Injection - Riskiluokka: $\color{red}{\textsf{High}}$ - 4 kpl
 - Pakotettu SQL komennon syöttäminen, jotta päästään tietokantoihin käsiksi.
 
Content Security Policy (CSP) Header Not Set - Riskiluokka: $\color{Yellow}{\textsf{Medium}}$ - 1 kpl
- Ei ole rajoitettu mistä sivusto saa ladata resursseja. Tämä voi johtaa mm: ulkoisen koodin syöttämisen palveluun.

Format String Error - Riskiluokka: $\color{Yellow}{\textsf{Medium}}$ - 1 kpl
 - Ohjelma saattaa lukea käyttäjän syöttämää teksiä formaattikomentona sen sijaan, että se käsittelisi sitä pelkkänä tekstinä.
 
Missing Anti-clickjacking Header - Riskiluokka: $\color{Yellow}{\textsf{Medium}}$ - 1 kpl
- Sivustoa ei ole suojattu "ClickJacking"- hyökkäykseltä, josta voi seurata tietojan kaappaaminen.

X-Content-Type-Options Header Missing - Riskiluokka: $\color{Green}{\textsf{Low}}$ - 3 kpl
- Otsikolle ei ole annettu "NoSniff" arvoa, jonka seurauksena selaimet voivat tulkita tietoa väärin ja täten käsitellä sitä väärin.

User Agent Fuzzer - Riskiluokka: $\color{Blue}{\textsf{Informational}}$ -  12 kpl
- Ohjelman vaste voi riippua siitä, millainen selain tai hakukone on käsittelemässä tietoa.


[ZAP-report](zap-report.md)
