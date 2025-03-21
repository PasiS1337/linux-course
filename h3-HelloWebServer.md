Pohjana Tero Karvinen 2025: Linux kurssi, http://terokarvinen.com

# Host-koneen specsit:

- Tietokoneen specsit: AMD Ryzen 7 5700X3D prosessori, RTX 4070 Super näytönohjain (12GB VRAM), 32GB RAM sekä B550M emolevy, 1TB SSD sekä Windows 11 Home OS.
- käytössä Debian-live-12.9.0-amd64-xfce versio
- RAM-allokointi virtuaalikoneelle: 8GB
- virtuaaliselle kovalevylle tilaa jaettu: 150GB
- VirtualBox-ohjelma käytössä

# x) tehtävä

-Nimipohjaiset virtuaalipalvelimet eroavat IP-pohjaisista virtuaalipalvelimista siten, että yhdellä IP-osoitteella voit hostata useampaakin verkkosivustoa, kun taas IP-pohjaisilla virtuaalipalvelimilla jokainen vaatii oman IP-osoitteen. Tämä vaatii joitain erillisiä DNS-konfiguraatioita toimiakseen.

# a) Tehtävä 

Asennettiin tuo Apache jo tunnin aikana komennolla $ sudo apt-get -y install apache2, ja menemällä browserissa http://localhost sain näkyviin sen default sivun, mikä näkyy kun Apache on onnistuneesti asennettuna, mutta alettiin jo tunnilla tekemään tuota name-based virtual hostia niin en saa nyt kuvaa siitä, mutta tälläinen sivu oli: (kuva: Stackoverflow:n sivulta) --elikkä asennus onnistui.

![Alt Text](images/Week3image1.jpg)

# b) tehtävä - lokit

![Alt Text](images/Week3image8.png)

tuo "GET / HTTP/1.1" 200 Meinaa, että HTTP GET requesti tehtiin sivulle, (sivu ladattiin), ja tuo numero 200 meinaa, että se oli onnistunut. (Lähde: https://askubuntu.com/questions/733265/what-is-get-http-1-1-200-19019) sen jälkeen oleva Mozzilla/5.0  on user agent, joka kertoo minkälaista ohjelmistoa selain käyttää. Seuraavaksi on X11; Linux x86_64. Tuo X11 on versio 11 X window systemistä, ja se on pala softaa joka kommunikoi todella alhaisella tasolla koneen video hardwaren kanssa ja näyttää ruudulla pikseleitä (tai näin ainakin itse ymmärsin sen)" (lähde: https://unix.stackexchange.com/questions/63550/x11-platform-in-google-account-activity)  Linux x86_64 on käyttöjärjestelmä, jolta requesti tuli.  

tuo rv:128: on revision number, ja jokaisella user-agentilla on oma erillinen numero, mistä erottaa mikä on mikäkin ja tuo Gecko on browser engine, jonka on kehittänyt Mozzilla ja se on käytössä firefoxissa sekä monissa muissa eri projekteissa (lähde: https://firefox-source-docs.mozilla.org/overview/gecko.html)  Firefox 128.0 kertoo selaimen, ja mikä versio selaimesta käytössä.





# c) ja e) tehtävä  --Name-based virtual hosting + valid html5 page

Aloitin menemällä /etc/apache2/sites-enabled ja käytin komentoa $ sudo a2dissite 000-default.conf, jolla otin sen default localhost sivun pois käytöstä ja tein sinne uuden tiedoston nimeltä hattu.example.com.conf. Sen jälkeen laitoin kyseisen tiedoston sisälle seuraavat tiedot:

![Alt Text](images/Week3image2.png)

Sen jälkeen komennolla $ sudo a2ensite hattu.example.com ja restarttia komennolla sudo systemctl restart apache2 ja tämän jälkeen kävin katsomas /etc/apache2/sites-enabled hakemistosta, että onko hattu.example.com.conf mennyt sinne niin sieltähän se löytyi. Seuraavaksi käyn tekemässä /home/pasis/publicsites hakemistoon tuon hattu.example.com hakemiston, ja sen sisälle index.html tiedoston (lähde: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

Sen jälkeen kävin netistä vaan googlaamalla default html page template, ja pastesin koodin sinne index.html tiedoston sisälle niin siitä saatiin tuo validi html5 sivu.

![Alt Text](images/Week3image3.png)

ja localhostiin menemällä browserissa näyttää nyt tältä

![Alt Text](images/Week3image4.png)

## Pieni error, minkä kohtasin (piti selvittää, ennenku pystyin tehä ton b) tehtävän

Elikkäs kun koitin alkaa tehdä tuota b) tehtävää (teen sen vasta noiden c) ja e) tehtävien jälkeen niin kun koitin saada noita lokitietoja näkyviin niin jostain syystä /var/log/apache2/access.logiin ei ilmestynyt yhtään uusia lokeja, vaikka shift-reloadilla koitin päivittää sekä localhost, että hattu.example.com sivua browserissa. Tämän jälkeen katsoin komennolla $ sudo apache2ctl configtest, jos löytyisi jotain mikä voisi selittää asian ja sinne ilmestyi tälläinen viesti

![Alt Text](images/Week3image5.png)

Tämän jälkeen googlasin kyseisen errorin, joka johti minut suoraan (https://www.digitalocean.com/community/tutorials/apache-configuration-error-ah00558-could-not-reliably-determine-the-server-s-fully-qualified-domain-name) -sivulle, josta löytyikin ohjeet, millä sain tuon errorin korjattua. Ohjeissa luki, että täytyy mennä /etc/apache2/apache2.conf tiedostoon ja tiedoston loppuun lisätä "ServerName 127.0.0.1" joten kävin tekemässä ton, ja sitten komennolla $ sudo apache2ctl configtest kyseinen error-viesti ei tullut enään näkyviin. 

![Alt Text](images/Week3image6.png)

nyt alkoi tulemaan access.logiin tietoja kun reloadasin sivua. Eli vissiin viimeisimmän apache2 restartin jälkeen alkoi toimia. 

![Alt Text](images/Week3image8.png)

# f) tehtävä -- 

Curl komennossa tuo aloitus c- meinaa, että se on client-sided ohjelma ja tuo URL lopussa (cURL) meinaa, että se toimii URLien kanssa lähettämällä/lataamalla dataa. Curl "insert-random-sivu-tähän" lataa sen sivun ja näyttää sen html-koodin suoraan terminaalissa. curl -I taas näyttää vain sivun header-tiedot (Lähde: https://supporthost.com/curl-command-linux/)

![Alt Text](images/week3image9.png)

# Lähteet

https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ <br>
https://httpd.apache.org/docs/2.4/vhosts/name-based.html <br>
https://www.digitalocean.com/community/tutorials/apache-configuration-error-ah00558-could-not-reliably-determine-the-server-s-fully-qualified-domain-name <br>
https://askubuntu.com/questions/733265/what-is-get-http-1-1-200-19019 <br>
https://firefox-source-docs.mozilla.org/overview/gecko.html <br>
https://supporthost.com/curl-command-linux/ <br>
https://terokarvinen.com/linux-palvelimet/#h3-hello-web-server <br>
