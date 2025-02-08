# H4

a)

Tässä harjoituksessa tarkoituksena oli vuokrata oma virtuaalipalvelin. Päätin vuokrata palvelimen UpCloudista. Ihan ensimmäisenä loin Upcloudissa käyttäjätilin. 

<img src="Accountverification.png" width="600" />

Seuraavaksi aloitin virtuaalipalvelimen käyttöönoton ja määrittelin siihen liittyvät asetukset. Aluksi valitsin palvelimen sijainniksi Helsingin. Plan-osiossa valitsin UpCloudin edullisimman palvelinpaketin, joka sisältää 1-core prosessoriytimen, 1 GB muistia ja 10 GB tallennustilaa hintaan 3 €/kk. Jätin automaattiset varmuuskopiot -osion sekä verkkoyhteydet -osion oletusasetuksille. Käyttöjärjestelmäksi valitsin Debian GNU/Linux 12 (Bookworm). Kirjautumistavaksi valitsin SSH-avaimen.

<img src="Sijainti.png" width="600" />
<img src="Plan.png" width="600" />
<img src="verkkoyhteys.png" width="600" />
<img src="käyttöjärjestelmä.png" width="600" />

Seuraavaksi oli aika luoda ssh-avain. Olen aiemmin asentanut OpenSSH-ohjelma, joten minun ei tarvinnut tehdä mitään asennustoimia. Aloitin suoraan komennolla ssh-keygen, joka generoi uuden ssh-avaimen. Avain koostuu julkisesta ja yksityisestä osasta, ja ne tallennettiin oletuksena hakemistoon /home/kosovare/.ssh/. Julkinen avain tallennettiin tiedostoon id_rsa.pub ja yksityinen avain tiedostoon id_rsa. Lopuksi hain julkisen ssh-avaimen micro-tekstieditorissa ja liitin sen UpCloudin käyttöliittymään.

  micro $HOME/.ssh/id_rsa.pub # -> tällä löytyi 

<img src="ssh.png" width="600" />
<img src="sshkeygen.png" width="600" />
  
<img src="shhonnistui.png" width="600" />
<img src="verkkopalvelinasennettu.png" width="600" />

b)

Tässä harjoituksessa tein virtuaalipavelimellani alkutoimet: suljin root-tunnuksen, laitoin tulimuurin päälle ja päivitin ohjelmat. 

Suljin root-tunnuksen opettajan ohjeiden mukaisesti seuraavien vaiheiden avulla:

<img src="rootinpoisto2.png" width="600" />

Root-tunnuksen poiston jälkeen lopputilanne oli seuraava: 

<img src="rootinpoisto.png" width="600" />



