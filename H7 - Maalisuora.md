# H7 - Maalisuora

## a)

Tässä harjoituksessa tarkoituksena oli kirjoittaa ja suorittaa "Hei maailma" -ohjelma kolmella eri ohjelmointikielellä. Valitsin kieliksi Bashin, Pythonin ja

### Bash

Aloitin Bashilla. Ensin loin uuden skriptitiedoston nano-editorilla komennolla nano myscript.sh. 

<img src="bash3.png" width="600" />

Tiedoston ensimmäiselle riville lisäsin shebang-rivin #!/bin/bash, joka kertoo, että skripti suoritetaan bashilla. Seuraavaksi kirjoitin tiedostoon rivit echo Hei maailma ja date, jotka tulostavat "Hei maailma" ja näyttävät nykyisen päivämäärän ja ajan. Tallensin tiedoston painamalla Ctrl + X, minkä jälkeen editorin alareunaan tuli kysymys "Save modified buffer?". Kirjoitin "y", ja tiedosto tallentui.

<img src="bash.png" width="600" />

Lopuksi tein skriptistä suoritettavan komennolla chmod +x myscript.sh. Tämän jälkeen ajoin skriptin komennolla ./myscript.sh.

<img src="bash2.png" width="600" />

### Python

Aloitin harjoituksen päivittämällä järjestelmän ohjelmistot ja asentamalla saatavilla olevat päivitykset komennoilla sudo apt update ja sudo apt upgrade. Seuraavaksi asensin Pythonin komennolla sudo apt install python3.

<img src="python.png" width="600" />

Testasin, että Python toimii komennolla python3 --version, joka palautti Pythonin versionumeron, mikä vahvistaa, että se on asennettu ja toimii oikein.

<img src="python2.png" width="600" />

Loin uuden python-tiedoston komennolla nano hello.py. Siirryin nano-editoriin ja kirjoitin seuraavan sisällön:

<img src="python3.png" width="600" />

Tallensin tiedoston, palasin komentoriville ja suoritin juuri luomani komennon komennolla python3 hello.py.

<img src="python4.png" width="600" />

### Ruby

Aloitin tämänkin harjoituksen ensin asentamalla uuden ohjelmointikielen Ruby komennolla sudo apt install ruby. Seuraavaksi loin ruby-tiedoston nano-editorilla komennolla nano hello.rb. Siirryin nano-editoriin ja kirjoitin tiedostoon seuraavan sisällön: 

<img src="ruby.png" width="600" />

Tallensin tiedoston ja palasin komentoriville, jossa suoritin komennon chmod +x hello.rb, joka teki tiedostosta suoritettavan. Tämän jälkeen ajoin komennon ./hello.rb, ja ohjelma tulosti "Hei maailma".

<img src="ruby3.png" width="600" />


Lähteet:

https://www.geeksforgeeks.org/custom-commands-linux-terminal/

https://www.geeksforgeeks.org/how-to-install-python-on-linux/

https://www.jcchouinard.com/create-python-script-from-terminal/

https://stackify.com/install-ruby-on-ubuntu-everything-you-need-to-get-going/#:~:text=Install%20Ruby%20on%20Ubuntu%20with%20APT%201%20Step,step%20is%20mostly%20for%20our%20own%20edification.%20

https://flatironschool.com/blog/building-your-first-command-line-application-in-ruby/

## c) Komento kaikille käyttäjille

Tässä harjoituksessa tavoitteena oli luoda uusi komento Linuxiin siten, että kaikki käyttäjät voivat käyttää sitä. Toteutin tämän aiemmin luomastani Bash-skriptistä (myscript.sh).

Kopioin skriptin järjestelmän hakemistoon komennolla sudo cp myscript.sh /usr/local/bin/myscript.

<img src="komentotoimii.png" width="600" />

Lopuksi testasin komennon toimivuuden. Suoritin komennon myscript, ja se tulosti odotetusti "Hei maailma" sekä nykyisen päivämäärän.

<img src="komentotoimii2.png" width="600" />

Lähteet: 

https://terokarvinen.com/2007/12/04/shell-scripting-4/

## d) Vanha laboratorioharjoitus

Tässä harjoituksessa ratkaisin vanhan laboratorioharjoituksen soveltuvin osin. Valitsin vuoden 2024 kevään kurssin laboratorioharjoituksen. Tein tehtävän d kurssilla käyttämälläni virtuaalikoneella. Seuraavia harjoituksia varten loin uuden virtuaalikoneen harjoitusta varten H1 - oma Linux -harjoituksen ohjeiden mukaisesti.  

### d) Howdy

Aloitin tehtävän luomalla nano-tiedosto "howdy.sh". Luotuani tiedoston kirjoitin siihen seuraavan sisällön: 

<img src="howdy1.png" width="600" />

Tallensin tiedoston, palasin komentoriville ja tein siitä suoritettavan komennolla chmod +x howdy.sh. 

<img src="howdy2.png" width="600" />

Sen jälkeen testasin skriptin toimivuuden suorittamalla komennon ./howdy.sh.

<img src="howdy3.png" width="600" />

Komento toimi kuten odotin, joten jatkoin tehtävää. Seuraavaksi tein siitä kaikkien käyttäjien käytettävissä olevan suorittamalla komennon sudo cp howdy.sh /usr/local/bin/howdy. Komentorivi pyysi salasanaa, jonka syötin. Lopuksi testasin komennon ajamalla komennon howdy.

<img src="howdy4.png" width="600" />

## e) 

Aloitin tehtävän luomalla uuden virtuaalikoneen ja suorittamalla tarvittavat alkumääritykset sekä päivitykset komentokehotteella. Päivitin järjestelmän ohjelmat komennolla sudo apt-get update ja sudo apt-get dist-upgrade. Asensin palomuurin komennolla sudo apt-get -y install ufw ja otin sen käyttöön komennolla sudo ufw enable. Lisäksi asensin nano-editorin tulevia tehtäviä varten komennolla sudo apt-get install nano.

Päivitysten ja asennusten jälkeen aloitin varsinaisen tehtävän asentamalla Apache-verkkopalvelimen komennolla sudo apt-get -y install apache2. Tämän jälkeen kirjoitin selaimen osoiteriville "http://localhost", ja pääsin Apachen aloitussivulle eli asennus oli onnistunut.

<img src="apachenasennusharjoitus.png" width="600" />

Muokkasin Apachen testisivua komennolla echo "AI Kakone" | sudo tee /var/www/html/index.html. Testasin muutosta avaamalla selaimessa "http://localhost", ja kirjoittamani teksti näkyi odotetusti.

<img src="aikakone.png" width="600" />

Seuraavaksi aloitin name-based virtual hostin luomisen. Ensin muokkasin Apache-verkkopalvelimen virtuaalipalvelimen asetuksia komennolla sudoedit /etc/apache2/sites-available/harjoitus.com.conf. Komento avasi nano-editorin, johon lisäsin seuraavan sisällön:

<img src="aikakone4.png" width="600" />

Tallennettuani konfiguraatiotiedoston palasin komentoriville ja otin muutokset käyttöön komennolla sudo a2ensite harjoitus.com sekä käynnistin Apachen uudelleen komennolla sudo systemctl restart apache2.

Seuraavaksi loin hakemiston sivustolle komennolla sudo mkdir -p /home/xubuntu/publicsites/harjoitus.com/ ja annoin kaikille käyttäjille luku- ja suoritusoikeudet komennolla sudo chmod ugo+rx /home/xubuntu/publicsites/harjoitus.com.

Tarkistin käynnissä olevat verkkosivut komennolla ls /etc/apache2/sites-enabled/ ja poistin oletussivun käytöstä komennolla sudo a2dissite 000-default.conf. Käynnistin Apachen uudelleen komennolla sudo systemctl restart apache2. Nyt vain itse luomani sivu (harjoitus.com) on käynnissä.

<img src="aikakone7.png" width="600" />

Jatkoin seuraavaksi luomalla html-tiedoston nano-editorissa komennolla nano /home/xubuntu/publicsites/harjoitus.com/index.html ja kirjoitin tiedostoon seuraavan sisällön:

<img src="aikakone8.png" width="600" />

Tallensin tiedoston (Ctrl + S) ja poistun editorista. Tämän jälkeen päivitin verkkoselaimessa localhost-sivun ja tarkistin, että muutokset näkyvät sivulla. Sivu näytti oikealta. 

<img src="aikakone2.png" width="600" />

Lähteet: 

https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-linux-palvelimet/
