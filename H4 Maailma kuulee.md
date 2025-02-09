# H4 - Maailma kuulee


##  x) Teoriasta käytäntöön pilvipalvelimen avulla (h4)

### a) Pilvipalvelimen vuokraus ja asennus:

1. Ensimmäiseksi tulee rekisteröityä palveluntarjoajan sivuille ja syöttää maksutiedot käyttäjätilin vahvistamiseksi. Kun käyttäjätili on valmis, luodaan uusi virtuaalikone esim. seuraavilla asetuksilla: käyttöjärjestelmäksi valitaan Debian 11 x64, valitaan resurssit 1 vCPU, 1 GB RAM, 25 GB SSD, datakeskuksen tulee olla mahdollisimman lähellä käyttäjiä (esim. Amsterdam) ja kirjautumistavaksi voi valita vahvan salasanan tai SSH-avaimen.
2. Palvelin luodaan ja palveluntarjoaja antaa sille julkisen IP-osoitteen, jonka avulla palvelimeen voi muodostaa yhteyden.
3. Seuraavaksi hankitaan domainnimi esim. Namecheapin kautta. Rekisteröitymisen jälkeen hallintapaneelista tulee poistaa automaattisesti luodut A Record- ja CNAME Record -tietueet. Domainin ohjaaminen palvelimeen tehdään lisäämällä uudet A Record -merkinnät, joissa arvoksi (Value) asetetaan palvelimen IP-osoite. TTL-arvoksi (Time-To-Live) suositellaan 5 minuuttia, jotta muutokset päivittyvät nopeasti.
4. Palvelin on valmiina käyttöön.

### d) Palvelin suojaan palomuurilla

Virtuaalipalvelimen suojaamiseksi on tärkeää ottaa käyttöön palomuuri. Palomuuri aktivoidaan seuraavasti: 

1. Muodostetaan ssh-yhteys palvelimeen käyttämällä sen ip-osoitetta. Tämä tapahtuu komentorivillä komennolla ssh root@PalvelimenIp-osoite. Yhteyttä luodessa järjestelmä kysyy varmistuksen, jonka jälkeen syötetään palvelimelle määritetty salasana.
2. Tarkistetaan saatavilla olevat päivitykset komennolla sudo apt-get update
3. Asennetaan palomuuri (UFW – Uncomplicated Firewall) komennolla sudo apt-get install ufw
4. Jotta SSH-yhteys säilyy palomuurin käyttöönoton jälkeen, avataan sille tarvittava portti (22/tcp) komennolla sudo ufw allow 22/tcp
5. Lopuksi otetaan palomuuri käyttöön komennolla sudo ufw enable. Tämän jälkeen palvelimen tietoliikennettä suojataan palomuurilla, joka estää tarpeettomat yhteydet ja sallii vain sallitut liikennemuodot.

### e) Kotisivut palvelimelle

Seuraavaksi asennetaan virtuaalipalvelimelle Apache-webpalvelin, korvataan testisivu, ja luodaan käyttäjälle toimiva kotisivu Internetiin.

1. Uuden käyttäjän luominen komennolla sudo adduser käyttäjänimi.
2. Annetaan pääkäyttäjäoikeudet komennolla sudo adduser käyttäjänimi ja määritetään vahva salasana.
3. Uuden käyttäjän tunnukset testataan avaamalla SSH-yhteys palvelimeen komennolla ssh käyttäjänimi@PalvelimenIp-osoite
4. Päivitetään palvelin komennolla sudo apt-get update
5. Lukitaan Root-käyttäjä komennolla sudo usermod --lock root
6. Testataan domainin reitityksen toimivuus komennolla ping oma-domain.fi
7. Palvelin päivitetään ennen web-palvelimen asennusta komennoilla sudo apt-get update, sudo apt-get upgrade ja sudo apt-get dist-upgrade
8. Asennetaan Apache-webpalvelin komennolla sudo apt-get install apache2
9. Tarkistetaan, että palvelimen tila on aktiivinen komennolla sudo systemctl status apache2
10. Määritellään palomuurin asetukset komennolla sudo ufw allow 80/tcp
11. Korvataan Apachen testisivu komennolla echo "Hello world!" | sudo tee /var/www/html/index.html
12. Käyttäjäkohtaisia sivuja varten aktivoidaan userdir-moduuli ja käynnistettiin Apache uudelleen komennoilla sudo a2enmod userdir ja sudo service apache2 restart
13. Käyttäjälle luodaan kotihakemistoon julkinen hakemisto komennolla mkdir -p /home/käyttäjänimi/public_html
14. Testataan selaimessa, että hakemisto näkyy osoitteessa oma-domain.fi/~käyttäjänimi
15. Tekstitiedostoja muokataan micro-editorilla, joka voidaan asentaa komennolla sudo apt-get install micro
16. Siirrytään käyttäjän julkiseen hakemistoon ja luodaan HTML-tiedosto komennoilla cd /home/käyttäjänimi/public_html ja micro index.html
17. Kirjoitetaan tiedostoon HTML-koodi, tallennetaan se ja suljetaan editori
18. Lopuksi kotisivujen näkyvyys testataan selaimella.

### f) Palvelimen ohjelmien päivitys

1. Palvelimen ohjelmat päivitetään avaamalla SSH-yhteys ja suorittamalla komennot sudo apt-get update, sudo apt-get upgrade ja sudo apt-get dist-upgrade  
2. Palvelimen kirjautumislokeja tutkitaan komennolla sudo less /var/log/auth.log | grep log. Lokeista löytyneen epäilyttävän tapahtuman tarkempi analysointi tehdään esim. komennolla sudo less /var/log/auth.log | grep 10540

### Lähteet:

Lehto S. Luettavissa: https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/. Luettu: 9.2.2025

## x) First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS

Virtuaalipalvelimen käyttöönotto alkaa seuraavilla ohjeilla:
1. Luodaan tili DigitalOceanissa, lisätään maksukortti ja/tai alennuskoodi. 
2. Luodaan uusi virtuaalipalvelin. Käyttöjärjestelmäksi valitaan Ubuntu 16.04 LTS. Datakeskuksen tulee sijaita lähellä asiakkaitasi, joten valitsemme Euroopan alueen. Kirjautumistavaksi valitaan SSH-avain, tai salasana, mikäli et osaa luoda ssh-avainta.
3. Tarkistetaan palvelimen IP-osoite.
4. Kirjaudutaan palvelimeen ensimmäistä kertaa käyttäen SSH:ta root-käyttäjänä. Tämä tapahtuu komennolla ssh root@PalvelimenIp
5. Asetetaan hyvä salasana

Palvelimen palomuurin asetukset on määritettävä oikein. Tämä tehdään seuraavalla tavalla:
1. Määritetään palomuurin asetukset komennoilla sudo ufw allow 22/tcp ja sudo ufw enable

Palvelimelle luodaan sudo-käyttäjä seuraavilla ohjeilla:
1. Luodaan uusi käyttäjä (esim. tero) komennoilla sudo adduser tero, sudo adduser tero sudo, sudo adduser tero adm ja sudo adduser tero admin
2. Testataan kirjautuminen uuteen käyttäjään toisessa terminaalissa ennen kuin suljetaan root-käyttäjän istunto
3. Muodostetaan ssh-yhteyd virtuaalipalvelimelle komennolla ssh tero@tero.example.com

Suljetaan root-käyttäjä:
1. Suljetaan root-käyttäjä komennolla sudo usermod --lock root
2. Estetään root-kirjautuminen SSH:ssa komennolla sudoedit /etc/ssh/sshd_config. Muokataan tiedostoa ja varmistetaan, että rivillä PermitRootLogin on arvo no.
3. Käynnistetään SSH-palvelu uudelleen komennolla sudo service ssh restart

Ohjelmien päivitys:
1. Päivitetään ohjelmat komennoilla sudo apt-get update ja sudo apt-get upgrade

Virtuaalipalvelimen käyttö:

Huom! Asentaessasi julkisen palvelimen, kuten Apache, muista avata palomuurissa tarvittavat portit komennolla sudo ufw allow 80/tcp
Nyt palvelin on valmiina käyttöön.

Julkisen DNS-nimen lisääminen NameCheapissa:
1. Lisätään verkkotunnus, jotta se on muille helpompi muistaa. Nimen vuokraaminen voidaan tehdä NameCheapissä tai Gandissa. Jos käyttää GitHub Education -pakettia, voi saada ehkä ilmaiseksi .me-verkkotunnuksen. Ohjeet verkkotunnuksen ohjaamiseen DigitalOceanin palvelimeen löytyvät NameCheapista. Lisätään uusi A-tietue (esim. "@").
2. Testataan verkkotunnuksen toimivuutta käyttämällä komentoa: host example.com dns1.registrar-servers.com
3. Käytetään Firefoxia vain, kun verkkotunnus on toiminut, jotta vanha nimi ei jää välimuistiin.

### Lähteet:

Karvinen T. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu 8.2.2025.

## a)

Tässä harjoituksessa tarkoituksena oli vuokrata oma virtuaalipalvelin. Päätin vuokrata palvelimen UpCloudista. Ihan ensimmäisenä loin Upcloudissa käyttäjätilin ja lisäsin maksukortin.

<img src="Accountverification.png" width="600" />

Seuraavaksi aloitin virtuaalipalvelimen käyttöönoton ja määrittelin siihen liittyvät asetukset. Palvelimen sijainniksi valitsin Helsingin. 

<img src="Sijainti.png" width="600" />

Plan-osiossa valitsin UpCloudin edullisimman palvelinpaketin, joka sisältää 1-core prosessoriytimen, 1 GB muistia ja 10 GB tallennustilaa hintaan 3 €/kk. 

<img src="Plan.png" width="600" />

 Jätin automaattiset varmuuskopiot -osion sekä verkkoyhteydet -osion oletusasetuksille. 
 
<img src="verkkoyhteys.png" width="600" />

Käyttöjärjestelmäksi valitsin Debian GNU/Linux 12 (Bookworm). 

<img src="käyttöjärjestelmä.png" width="600" />

 Kirjautumistavaksi valitsin SSH-avaimen. Huom. lisäsin SSH-avaimen UpCloudiin vasta seuraavan kohdan jälkeen, kun olin luonut sen komentorivillä. 
 
<img src="shhonnistui.png" width="600" />

Seuraavaksi oli aika luoda ssh-avain. Olen aiemmin asentanut OpenSSH-ohjelman, joten minun ei tarvinnut tehdä mitään asennustoimia. Aloitin suoraan komennolla ssh-keygen, joka generoi uuden ssh-avaimen. Avain koostuu julkisesta ja yksityisestä osasta, ja ne tallennettiin oletuksena hakemistoon /home/kosovare/.ssh/. Julkinen avain tallennettiin tiedostoon id_rsa.pub ja yksityinen avain tiedostoon id_rsa. Lopuksi hain julkisen ssh-avaimen micro-tekstieditorissa komennolla micro $HOME/.ssh/id_rsa.pub #, ja liitin sen UpCloudin käyttöliittymään (edellinen kuva).

<img src="sshkeygen.png" width="600" />

Lopuksi klikkasin UpCloudin liittymän vasemmassa alareunassa olevaa "Deploy" painiketta, joka käynnisti virtuaalipalvelimen luomisen ja palvelimen ip-osoite muodostui. 

<img src="verkkopalvelinasennettu.png" width="600" />

## b)

Tässä harjoituksessa tein virtuaalipavelimellani alkutoimet: suljin root-tunnuksen, laitoin palomuurin päälle ja päivitin ohjelmat. 

Suljin root-tunnuksen opettajan ohjeiden mukaisesti seuraavien vaiheiden avulla:

<img src="rootinpoisto2.png" width="600" />

Root-tunnuksen poiston jälkeen lopputilanne oli seuraava: 

<img src="rootinpoisto.png" width="600" />

Jatkoin seuraavaksi tulimuurin käynnistämisellä. Aloitin päivittämällä ohjelmat ja paketit komennolla sudo apt-get update. Kun päivitys oli valmis, asensin palomuurin komennolla sudo apt-get install ufw.

<img src="palomuuri.png" width="600" />

Ennen tulimuurin käynnistämistä tein siihen reiän komennolla sudo ufw allow 22/tcp. Käynnistin tulimuurin lopuksi komennolla sudo ufw enable. 

<img src="palomuuri.png" width="600" />

Lopuksi päivitin palvelimeni ohjelmat komennoilla sudo apt-get update ja sudo apt-get upgrade. Lisäksi suoritin komennon sudo apt-get dist-upgrade, joka päivittää ohjelmat ja paketit kattavammin.

## c)

Tässä harjoituksessa asensin virtuaalipalvelimelleni oman web-palvelimen (Apache), ja korvasin sen oletussivun. Apachen asennus alkoi komennolla sudo apt-get install apache2. Seuraavaksi käynnistin apachen komennolla sudo systemctl start apache2 ja tarkistin, että palvelin oli käynnissä osoitteella http://94.237.12.170, jolloin näkyi Apache:n oletustestisivu. 

Tämän jälkeen muokkasin sivua. Apache:n oletussivun tiedosto sijaitsee /var/www/html/index.html, ja korvasin sen omalla HTML-sivullani. Avasin tiedoston tekstieditorilla komennolla sudo nano /var/www/html/index.html ja lisäsin siihen oman sisällön. Lisäksi avasin palomuurissa portin 80 komennolla sudo ufw allow 80/tcp.

<img src="apachenasennus2.png" width="600" />
<img src="apachenasennus3.png" width="600" />

Kun olin tallentanut oman sivuni, kokeilin, että se näkyy julkisesti kirjoittamalla palvelimen IP-osoitteen selaimeen (http://94.237.12.170/).

<img src="Testisivu2.png" width="600" />

Testasin lopuksi sivun toimivuutta vielä omalla puhelimellani. Sivu toimi odotetusti. 

<img src="testipuhelimella.png" width="600" />

### Lähteet:

Karvinen T. Luettavissa: https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/. Luettu 8.2.2025.
Karvinen T. Luettavissa: https://terokarvinen.com/linux-palvelimet/#h4-maailma-kuulee. Luettu 8.2.2025.

