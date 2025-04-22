### Cisco Cybersecurity.

![!\[\[Cisco-course.png\]\] ](Cisco-course.png)

Tällä kurssilla oli tietoturvallisuuden perusteisiin liittyviä asioita.
Mitä on kuberturvallisuus ja kuinka tunnistan kyberhyökkäyksen? Avattiin termiä "Cyberwarfare".
Kuinka suojaudun kyberturvallisuus hyökkäyksiltä ja kuinka hakkeri voi hyväksi käyttää tietojani. 
Millaista tietoa tallennetaan ja mihin tietoa saadaan tallentaa. Kenellä on pääsy tietoihini. 
Organisaatioiden turvaaminen ja millaista uraa voi kehittää tietoturvallisuuspuolella. 
Lisäksi erilaisia kyberhyökkäystapoja ja tapoja suojautua niiltä.

### Portswigger.

![!\[\[Dashboard.png\]\]](Dashboard.png)
Tehdyt labrat:
1. SQL-injection
	1. [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)
	2. [SQL injection vulnerability allowing login bypass](https://portswigger.net/web-security/sql-injection/lab-login-bypass)
2. Cross-site scripting
	1. [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)
	2. [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)
3. Cross-site request forgery (CSRF)
	1. [CSRF vulnerability with no defenses](https://portswigger.net/web-security/csrf/lab-no-defenses)
	2. [CSRF where token validation depends on request method](https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-request-method)
4. Clickjacking
	1. [Basic clickjacking with CSRF token protection](https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected)
	2. [Clickjacking with a frame buster script](https://portswigger.net/web-security/clickjacking/lab-frame-buster-script)
5. DOM-based vulnerabilities
	1. [DOM XSS using web messages](https://portswigger.net/web-security/dom-based/controlling-the-web-message-source/lab-dom-xss-using-web-messages)
	2. [DOM-based cookie manipulation](https://portswigger.net/web-security/dom-based/cookie-manipulation/lab-dom-cookie-manipulation)
6. Cross-origin resource sharing (CORS)
	1. [CORS vulnerability with basic origin reflection](https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack)
	2. [CORS vulnerability with trusted null origin](https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack)
7. Access control vulnerabilities
	1. [Unprotected admin functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)
	2. [Unprotected admin functionality with unpredictable URL](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url)
8. Authentication
	1. [Username enumeration via different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)
	2. [2FA simple bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)
9. API testing
	1. [Exploiting an API endpoint using documentation](https://portswigger.net/web-security/api-testing/lab-exploiting-api-endpoint-using-documentation)
	2. [Finding and exploiting an unused API endpoint](https://portswigger.net/web-security/api-testing/lab-exploiting-unused-api-endpoint)

Portswigger aktiviteetissa heräsi siihen, että kuinka monella tapaa sivustoa voidaan "härnätä" ja kuinka helppoa on tehdä ns.paska sivusto. Kanssa opiskelijalta sain kuulla, että labrat toistaa itseään aika usein tietyn aiheen alla joten päätin ottaa labroja sieltä täältä. Erikoista oli nähdä kuinka saatavilla työkalut tietoturvan haastamiseen oli. joissain tapauksissa riitti selain. Taikka heitetään API pyyntö serverille jolla voitiin poistaa käyttäjiä. 

### Tangentti.
Tässä kirjoittaessa tuli mieleen erään "kuuluisan" lukkosepän seminaari jossa hän puhuu turvallisuudesta tietoturva- aiheisessa seminaarissa. sisällöstä lyhyesti: hän mainitsee, että lukko on yhtä turvallinen, kun sen heikoin osa ja hän tekee yhteyden tietoturvaan johon sama sääntö pätee. Lisäksi hän sanoo että "Ei lukoista tule turvallisempia, jos/kun niiden heikkuksista ei kerrota. ihmisten tietoisuus turvallisuudesta parantaa ihmisten valintaa oikeanlaiseen turvallisuuteen"
[Keynote - LockPickingLawyer](https://www.youtube.com/watch?v=IH0GXWQDk0Q)

### Booking system project.

1. Phase 1.
	Tässä ehkä päällimmäisenä oli luoda testausympäristö johon kuului Kali- linux asennus.
	Sekä Zap testiympäristön käyttöä joka automatisoi penetraatiotestauksen osia. Mulla taisi olla kaikkein haastavin asentaa Kalilinux jossa piti se muutaman kerran asentaa.
2. Phase 2.
	Tässä oli salattujen salasanojen sevittämistä erinäisillä työkaluilla. Erityisesti HashCat. (Ronklasin myös JohnTheRipperiä mutta tulokset ei olleet mainittavia.) Annettujen arvojen avulla näiden MD5 hashausten purkaminen onnistui kohtuullisessa ajassa .
	Part2: Burb:in ja Hydran avulla dictionary ja non dictionary attack(bruteforce).
	Tässä noiden john ripperin kanssa touhaaminen oli vaikeaa. mitä löyty ja mihin se tieto tallennettiin. 
3. Phase 3.
	Autentikointi... No otettiin erilaisia rooleja koitettiin mihin niillä rooleilla pääsee. 
	Vierailija, Käyttäjä ja "hallitsija". Käyttäjät pyrkii toistensa tietoihin ja hallitsijat pyrkii toistensa tietoihin ja lopulta annetut roolit eivät olekkaan niin erilaisia toisistaan vaikka niillä tulisi olla selkeät erot.
4. Phase 4.
	GDBR. Mihin käyttäjien tietoja tallennetaan, miten niitä käytetään. onko tietojen hallintaan liittyvät asiat esitetty käyttäjille heille kuuluvilla tavalla? Täyttääkö demosivuto esitetyt vaatimukset.

Nämä tehtävät olivat hyviä, haastavia ja opettavaisia. niiden tekeminen oli mielekästä(paitsi kun kaliOS oli mennyt start/stop- looppiin jonka selvitys vei hieman aikaa(uusi asennus+reboot)).
Videoiden avulla osaamatonkin sai tehtävän tehtävän tehtyä, mutta aikaa ja työtä sekin vaati. Sekä mikään ohjelma ei mahdollista tehtävän tekemistä puolestani. 


### Logbook

[Cybersecurity/README.md at main · zuhazuzu/Cybersecurity](https://github.com/zuhazuzu/Cybersecurity/blob/main/README.md)

Kokonaisaika 61h.

Cisco - 6h.
Portswigger - 12.5h.
Phase 1- 7h.
Phase 2 - 9h.
Phase 3 - 4h.
Phase 4 - 4h.

Lokikirjan tekeminen palautti mukavasti mieleen asioita joita käsiteltiin. Itellä lokikirja oli paikallisesti Obsidian ohjelmassa josta ne sai helposti .md muotoon. joten sen päivitys GitHub:iin ei ollut aina ihan ajallaan. En kyllä osaa sanoa mitä tästä lokikirjan pitämisestä opin. Voiko sanoa että opin pitämään lokikirjaa? 

### Palaute. 

Kurssi on ollut tämän periodin parhaita toteutuksia. 
Parannusehdotuksiin olisin toivonut hieman syvällisempää palautetta tehtävistä. Toisaalta olisiko niiden antaminen muuttanut ulosantiani taikka latistanut asennettani kurssia kohtaan?