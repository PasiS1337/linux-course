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

Asennettiin tuo Apache jo tunnin aikana komennolla $ sudo apt-get -y install apache2, ja menemällä browserissa http://localhost sain näkyviin sen default sivun, mikä näkyy kun Apache on onnistuneesti asennettuna, mutta alettiin jo tunnilla tekemään tuota name-based virtual hostia niin en saa nyt kuvaa siitä, mutta tälläinen sivu oli: (kuva otettu netistä) 

![Alt Text](images/your-image-name.png)






# Lähteet

https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/ 
https://httpd.apache.org/docs/2.4/vhosts/name-based.html

