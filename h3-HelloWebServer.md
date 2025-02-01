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

----------------------LAIT TÄHÄN SITKU SAAN TON NAME BASED VIRTUAL HOSTIN TEHTYY NI TIETOO NIIST LOKEIST--------

# c) ja e) tehtävä  --Name-based virtual hosting + valid html5 page

Aloitin menemällä /etc/apache2/sites-enabled ja käytin komentoa $ sudo a2dissite 000-default.conf, jolla otin sen default localhost sivun pois käytöstä ja tein sinne uuden tiedoston nimeltä hattu.example.com.conf. Sen jälkeen laitoin kyseisen tiedoston sisälle seuraavat tiedot:

![Alt Text](images/Week3image2.png)

Sen jälkeen komennolla $ sudo a2ensite hattu.example.com ja restarttia komennolla sudo systemctl restart apache2 ja tämän jälkeen kävin katsomas /etc/apache2/sites-enabled hakemistosta, että onko hattu.example.com.conf mennyt sinne niin sieltähän se löytyi. Seuraavaksi käyn tekemässä /home/pasis/publicsites hakemistoon tuon hattu.example.com hakemiston, ja sen sisälle index.html tiedoston (lähde: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

Sen jälkeen kävin netistä vaan googlaamalla default html page template, ja pastesin koodin sinne index.html tiedoston sisälle niin siitä saatiin tuo validi html5 sivu.

![Alt Text](images/Week3image3.png)

ja localhostiin menemällä browserissa näyttää nyt tältä

![Alt Text](images/Week3image4.png)

Elikkäs kaikki toimii niinkuin pitääkin






# Lähteet

https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ 
https://httpd.apache.org/docs/2.4/vhosts/name-based.html

