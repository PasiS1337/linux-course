Pohjana Tero Karvinen 2025: Linux kurssi, http://terokarvinen.com

# Host-koneen specsit:

- Tietokoneen specsit: AMD Ryzen 7 5700X3D prosessori, RTX 4070 Super näytönohjain (12GB VRAM), 32GB RAM, B550M emolevy, 1TB SSD sekä Windows 11 Home OS.
- käytössä Debian-live-12.9.0-amd64-xfce versio
- RAM-allokointi virtuaalikoneelle: 8GB
- virtuaaliselle kovalevylle tilaa jaettu: 150GB
- VirtualBox-ohjelma käytössä

# x) tehtävä

a) Susanna Lehto hyödyntää Github Education pakettia, ja tästä syystä vuokraa DigitalOceanista Virtual Private Serverin. Hän on lisännyt kuvia prosessin aikana, joissa kertoo mitä asetuksia hän valitsee (Datakeskus mahd. läheltä sijaintia, storagen määrä ynms). Tämän jälkeen hän näyttää vielä miten domain nimi vuokrataan namecheapin kautta, myös käyttäen github educationin alennuskoodia.

d) Hän ottaa ekaksi SSH-yhteyden juuri vuokraamansa virtuaalipalvelimen IP-osoitteeseen, ja sen jälkeen lataa sekä asentaa ufw-palomuurin ja avaa tarvittavat portit, jolloinka muutamalla komennolla saadaan mahdollisten hyökkääjien työtä vaikeutettua huomattavasti (Lähde: Tero Karvisen luento sekä https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/) --Seuraavassa kohdassa hän jo huomaa, että joku kiinalainen botti oli yrittänyt päästä käsiksi hänen juuri vuokraamaansa virtuaalipalvelimeen, mutta vahvan salasanan sekä palomuurin takia tämä jäi vain yritykseksi. 

e) Seuraavaksi Susanna asentaa apache web-palvelimen sekä korvaa sen default-etusivun tekemällä uuden perus html-sivun.

f) Susanna asentaa uusimmat päivitykset virtuaalipalvelimelleen


# a) tehtävä - Virtuaalipalvelimen vuokraus (DigitalOcean)

Aloitin rekisteröitymällä DigitalOcean.com -sivulle, ja sen jälkeen linkitin GitHub-education accountin tuohon DigitalOcean accounttiin, jonka jälkeen sain viestin, että 200$ arvosta credittejä on annettu käyttöön seuraavan vuoden ajaksi. 
Sen jälkeen menin kohtaan Droplets (jostain syystä VPS on nimellä droplets-tällä sivustolla) ja lähdin valitsemaan minkälaisen virtuaaliserverin haluan vuokrata, ja tottakai tälleen ensikertalaisena ja testaamiskäyttöön valitsin halvimman, joka on 6$/kk tällä hetkellä. 

![Alt Text](images/Week4image1.png)

Seuraavaksi sain valita kirjautumisen ssh-avaimella tai salasanalla, ja kuten tunnilla näytettiin, asensin ensiksi $ sudo apt-get install openssh-client ja sen jälkeen komennolla $ ssh-keygen loin itselleni ssh-avaimen ja tämän jälkeen kyseinen public-key pitää copy pastee /home/pasis/.ssh/id_rsa.pub tiedostosta tuonne digitaloceanin sivulle.

![Alt Text](images/Week4image2.png)




# Lähteet
https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/ <br>
