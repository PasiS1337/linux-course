Pohjana Tero Karvinen 2025: Linux kurssi, http://terokarvinen.com

# Host-koneen specsit:

- Tietokoneen specsit: AMD Ryzen 7 5700X3D prosessori, RTX 4070 Super näytönohjain (12GB VRAM), 32GB RAM, B550M emolevy, 1TB SSD sekä Windows 11 Home OS.
- käytössä Debian-live-12.9.0-amd64-xfce versio
- RAM-allokointi virtuaalikoneelle: 8GB
- virtuaaliselle kovalevylle tilaa jaettu: 150GB
- VirtualBox-ohjelma käytössä

# a) Tehtävä - Domainin vuokraaminen (Namecheap)

Näköjään Namecheap ei ainakaan toimi Github educationin kanssa (Your university is not eligible) joten aloitin laittamalla oman nimeni Namecheapin domain searchiin ja sieltä tuli monta eri vaihtoehtoa, joista päätin valita pasisalmela.pro:n
<br>
![Alt Text](images/Week5image2.png)
<br>
<br>
Seuraavaksi menin Advanced DNS asetuksiin, ja laitoin samat asetukset mitä tunnilla käytiin läpi osoittamaan domain nimeni (pasisalmela.pro:n) tuohon virtuaalipalvelimeni IP-osoitteelle 134.122.56.192. 

![Alt Text](images/Week5image3.png)

Tämän jälkeen kävin katsomassa whatsmydns.net -sivulta, että onnistuiko tämä ja sinne alkoi pikkuhiljaa tulla eri servereille näkyviin tuo. 
<br>
<br>
![Alt Text](images/Week5image4.png)
<br>
<br>
Seuraavaksi kävin kokeilemassa pasisalmela.pro koneeni selaimella, ja sieltä tuli se viime tunnilla tehty testisivu näkyviin.

![Alt Text](images/Week5image5.png)
<br>
<br>

# b ja c) tehtävät (Name based virtual host ja kotisivut)

Olin jo aikaisemmalla kurssilla käyttänyt hyvän tovin aikaa kotisivujen tekemiseen, joten en viittinyt alkaa väsäämään uusiksi tyhjästä noita sivuja vaan kopioin tuolta mun githubista index.html, portfolio.html, services.html sekä styles.css tiedostot ja kävin tekemässä ne tiedostot tuonne /home/pasi/publicsites/pasiboi hakemistoon ja pastesin koodit niiden sisälle. <br>
<br>

![Alt Text](images/Week5image6.png)
<br>
<br>

 Tältä näyttää kotisivut sen jälkeen (background-imaget puuttuvat, mutta ei varsinaisesti olennaisesta tässä tehtävässä ---> lisään myöhemmin jos muistan/jaksan)
<br>
<br>
![Alt Text](images/Week5image7.png)
<br>
<br>
## Seuraavaksi käyn tekemässä subdomainit

Navigoin takas namecheapin sivulle, ja menin siellä kohtaan domain list --> domain --> Advanced DNS. Kävin lisäämässä sinne services sekä portfolio domainit, minkä pitäisi sitten toimia services.pasisalmela.pro ja portfolio.pasisalmela.pro subdomaineina. (Lähde: https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/)
<br>
<br>
![Alt Text](images/Week5image8.png)
<br>
<br>
Sitten kävin etsimässä netistä, että miten saan ne subdomainit aktivoitua, että kun menen esim. tonne services.pasisalmela.pro niin se näyttää sen sivun ja löysin tälläiset ohjeet https://dev.to/tikam02/configuring-domains-and-sub-domains-in-apache-webserver-1bl1 <br>
<br>
Sitten menin /etc/apache2/sites-enabled/pasiboi.conf tiedostoon ja lisäsin sinne tuon uuden subdomainin, yllä olevan linkin ohjeiden mukaan 

![Alt Text](images/Week5image9.png)

<br>
Tämän jälkeen tein tuon services subdomainin samalla kaavalla samaan tiedostoon ja sitten kävin testaamassa niin tuo subdomain toimii (tosin se vie vain kotisivulle mutta ohjeissa sanottiin, että tämä riittää).
<br>
<br>

![Alt Text](images/Week5image10.png)

# e) tehtävä -- host ja dig-komennot

Aloitin katsomalla man host ja man dig -sivut, mutta man dig ei näyttänyt mitään niin kävin katsomassa ja se pitää ensiksi asentaa. 
<br>
<br>
![Alt Text](images/Week5image11.png)
<br>
Vaikuttaa siltä, että host-komento on vähän "heikompi" versio dig:istä, ja sillä ei saa niin paljoa tietoa kuin digillä sivustoiden domain name serveristä. <br>
<br>
![Alt Text](images/Week5image12.png)
<br>
Tuo Time-to-live on namecheap.comilla 60, ja pasisalmela.pro:ssa 1799, mikä vaikuttaa aika suurelta erolta
<br>
<br>
Sitten kävin etsimässä jonkun pienen/keskipienen yrityksen, ja katsoin digillä niiden DNS-tietoja ja huomasin, että heillä on 2 eri IPv4 osoitetta (en osaa kyllä sanoa miksi, esim namecheap.comilla oli vain 1)
<br>
<br>
![Alt Text](images/Week5image13.png)
<br>
<br>
Sitten katsoin digillä redditin tietoja, ja huomasin, että redditillä on 4 eri IPv4 ja 4 eri IPv6-osoitetta
<br>
<br>
![Alt Text](images/Week5image14.png)




# Lähteet
https://terokarvinen.com/linux-palvelimet/#h5-nimekas <br>
https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ <br>
https://www.namecheap.com/support/knowledgebase/article.aspx/767/10/how-to-change-dns-for-a-domain/ <br>
https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/ <br>
https://dev.to/tikam02/configuring-domains-and-sub-domains-in-apache-webserver-1bl1 <br>
https://phoenixnap.com/kb/linux-dig-command-examples
https://www.tecmint.com/install-dig-and-nslookup-in-linux/#digdebian



