# H6 - Salataampa

## x)

### Lets encrypt

Let's Encrypt ja ACME-protokolla mahdollistavat HTTPS-palvelimen ja selainluotetun varmenteen automaattisen käyttöönoton ilman ihmisen väliintuloa. Prosessi etenee seuraavasti:

1. Let's Encrypt tunnistaa palvelimen ylläpitäjän julkisen avaimen avulla. Ensimmäisellä käyttökerralla agenttiohjelma luo avainparin ja todistaa varmenteen myöntävälle taholle (CA), että palvelin hallitsee domainia.

2. CA antaa agentille haasteen domainin hallinnan varmistamiseksi. Haaste voi olla esimerkiksi tietyn DNS-tietueen lisääminen domainin alle. Samalla CA toimittaa agentille merkkijonon (nonce), joka on allekirjoitettava yksityisellä avaimella avainparin hallinnan varmistamiseksi.

3. Kun agentti on suorittanut haasteen CA tarkistaa annetut tiedot, ja jos kaikki on oikein, se myöntää agentille oikeuden hallita domainiin liittyviä varmenteita.

Kun agentti on valtuutettu, varmenteiden pyytäminen, uusiminen ja peruuttaminen on yksinkertaista: oikea pyyntö lähetetään CA:lle ja agentti allekirjoittaa sen valtuutetulla avaimella.

Lähde: https://letsencrypt.org/how-it-works/

### Using an existing, running web server

Jos sinulla on jo verkkosivusto, joka toimii portissa 80, käytä --http ja --http.webroot -asetuksia. Näin ohjelma tallentaa haasteen tiedoston .well-known/acme-challenge -hakemistoon ilman, että palvelinta käynnistetään. Hakemiston täytyy olla julkisesti näkyvissä verkkosivulla. Jos se ei ole, pyynnöt voi ohjata oikeaan hakemistoon komennolla lego --accept-tos --email you@example.com --http --http.webroot /path/to/webroot --domains example.com run.

Lähde: https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server

### Basic Configuration Example

Esimerkki peruskonfiguraatiosta:

LoadModule ssl_module modules/mod_ssl.so

Listen 443

<VirtualHost *:443>

    ServerName www.example.com
    
    SSLEngine on
    
    SSLCertificateFile "/polku/www.example.com.cert"
    
    SSLCertificateKeyFile "/polku/www.example.com.key"

</VirtualHost>

Lähde: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

## a)




