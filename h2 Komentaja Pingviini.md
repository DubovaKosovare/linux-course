# H2 - Komentaja Pingviini

### x) Command Line Basics Revisited -tiivistelmä

Komentorivi on tietokoneen käyttöliittymä, jossa käyttäjä antaa tekstimuotoisia komentoja. Näillä komennoilla ohjataan tietokonetta suorittamaan haluttuja toimintoja. Seuraavaksi esitellään muutamia tärkeitä komentoja, joilla aloittaa komentorivin käytön: 

- pwd: tulostaa nykyisen hakemiston polun
- ls: listaa työhakemistossa olevat tiedostot 
- dc: vaihtaa hakemistoa 
- mkdir: luo uuden hakemiston
- rm: poistaa tiedoston
- man ls: tulostaa manuaalisivun
- history: tulostaa komentohistorian

On tärkeää ymmärtää hakemistorakennetta, jotta komentokehotteen komentoja ja tulosteita osaa tulkita oikein:  

- / on juurihakemisto
- /home/ sisältää kotihakemiston
- /home/kosovare/ on käyttäjän "kosovare" henkilökohtainen kotihakemisto
- /etc/ sisältää järjestelmän asetustiedostot
- /media/ on tarkoitettu irrotettavaille tallennusvälineille (esim. USB)
- /var/log/ sisältää järjestelmän lokitiedostot 

Sudo-komento suorittaa järjestelmän toimintoja, jotka vaativat korkeampia oikeuksia, ja niitä voi käyttää vain sudo-oikeudet omaava käyttäjä.

  - sudo apt-get update: päivittää pakettien saatavuuslistan
  - sudo apt-get -y install nethack-console: asentaa ohjelmiston
  - sudo apt-get purge nethack: poistaa ohjelmiston ja sen asetukset

### a) Micro

Tässä harjoituksessa asensin micro-editorin komentorivillä käyttämällä komentoa sudo apt-get install micro.

<img src="Micro.png" width="600" />

Asennuksen jälkeen testasin micro-editorin toimivuutta suorittamalla komennon micro --version.

<img src="micro2.png" width="600" />

### b) Apt

Asensin kolme uutta ohjelmaa komentorivillä: htop, tree ja steam locomotive. Asensin ohjelmat yksitellen tehtävää varten. Kaikki kolme ohjelmaa voidaan kuitenkin asentaa yhtä aikaa yhdellä komennolla. Tämä onnistuu seuraavasti:

sudo apt update
sudo apt install htop tree locomotive

#### htop
Htop on tekstipohjainen prosessinhallintaohjelma, joka näyttää järjestelmän tilan tietoja ja mahdollistaa prosessien tarkastelun sekä hallinnan. Asensin htop-ohjelman komennolla sudo apt install htop.

<img src="apt.htop.png" width="600" />

#### tree
Tree on ohjelma, joka näyttää tiedostojen ja hakemistojen rakenteen puumaisena luettelona. Asensin tree-ohjelman komennolla sudo apt install tree.

<img src="puu.png" width="600" />

#### steam locomotive
Steam locomotive on ohjelma, joka näyttää liikkuvan junan komentokehotteessa. Asensin sl-ohjelman komennolla sudo apt install locomotive.

<img src="locomotive.png" width="600" />

### c) FHS

Seuraavassa harjoituksessa tehtävänä oli esitellä tärkeät kansiot, jotka olivat listattuina Command Line Basics Revisited artikkelissa. 

<img src="Juuri.png" width="600" />
<img src="koti.png" width="600" />
<img src="kosovare.png" width="600" />
<img src="etc.png" width="600" />
<img src="media.png" width="600" />
<img src="log.png" width="600" />

### d) The Friendly M

<img src="mangrep1.png" width="600" />
<img src="mangrep2.png" width="600" />
<img src="mangrep3.png" width="600" />

### e) Pipe

<img src="putki.png" width="600" />

### f) Rauta

<img src="lshwAsennus.png" width="600" />


<img src="lshwTuloste.png" width="600" />

H/W path: kertoo laitteen sijainnin tietokoneessa
Device: laitteen nimi
Class:  laitteen luokka 
Description: kuvaus laitteesta



Lähteet: 

Tree command in Linux with examples. Luettavissa: https://www.geeksforgeeks.org/tree-command-unixlinux/. Luettu 26.1.2025.
Bohn K. 10.2.2020. A Beginners Guide to htop for Process Management. Luettavissa: https://spin.atomicobject.com/htop-guide/. Luettu: 26.1.2025.
Piping in Unix or Linux. Luettavissa: https://www.geeksforgeeks.org/piping-in-unix-or-linux/. Luettu: 26.1.2025. 
McKay C. 10.9.2023. How to use the grep command on Linux. Luettavissa: https://www.howtogeek.com/496056/how-to-use-the-grep-command-on-linux/. Luettu 26.1.2025.
Gite V. 14.9.2023. How to install wget on a Debian or Ubuntu Linux.Luettavissa: 
How to install "tree" with command-line?. Luettavissa: https://askubuntu.com/questions/572093/how-to-install-tree-with-command-line. Luettu: 25.1.2025.
Gite V. 21.6.2024. How to install htop on Ubuntu Linux using apt. Luettavissa: https://www.cyberciti.biz/faq/how-to-install-htop-on-ubuntu-linux-using-apt/. Luettu 25.1.2025.
r00t. How To Install Micro Text Editor on Debian 12. Luettavissa: https://idroot.us/install-micro-text-editor-debian-12/. Luettu 25.1.2025.
Cocca G. 5.4.2022. Command Line for Beginners – How to Use the Terminal Like a Pro [Full Handbook]. Luettavissa: https://www.freecodecamp.org/news/command-line-for-beginners/. Luettu 25.1.2025.
