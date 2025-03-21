Pohjana Tero Karvinen 2025: Linux kurssi, http://terokarvinen.com

# Host-koneen specsit:

- Tietokoneen specsit: AMD Ryzen 7 5700X3D prosessori, RTX 4070 Super näytönohjain (12GB VRAM), 32GB RAM sekä B550M emolevy, 1TB SSD sekä Windows 11 Home OS.
- käytössä Debian-live-12.9.0-amd64-xfce versio
- RAM-allokointi virtuaalikoneelle: 8GB
- virtuaaliselle kovalevylle tilaa jaettu: 150GB
- VirtualBox-ohjelma käytössä


# h2 x) tehtävä

-Tero on tehnyt sivun (https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited), johon hän on koonnut kaikista tärkeimmät Linux-komennot, jotka ovat olleet käytössä jo ennen internettiä. Se, että ne ovat vieläkin käytössä on todiste siitä, että ne on suunniteltu erittäin hyvin koska melkein kaikki tech-alalla oleva muuttuu jopa muutamissa vuosissa huomattavasti, puhumattakaan kymmenistä vuosista. Henkilökohtaisesti yllätyin, kuinka yksinkertaisilta nuo Linuxin file directoryt näyttävät Windowssiin verrattuna. Windowssissa joudut melkein aina googlaamaan, missä tietyt syvällä olevat tiedostot sijaitsevat directoryssä (ja missä directoryssä), koska niitä on mahdotonta muistaa jos koneella on enemmän ohjelmia asennettuna. 

# a) ja b) tehtävät: Micron, VLC:n, Terminator:in sekä Audacity:n asentaminen + testaus

a) Asensin Micro-tekstieditorin jo viime tunnin aikana komennolla "sudo apt install micro".

![Alt Text](images/MicroImage1.png)

b) "https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited" aivan viimeisellä rivillä mainitaan, että voit asentaa monta eri ohjelmaa käyttämällä komentoa $ sudo apt-get -y install x y z ------xyz korvataan toki ohjelmien nimillä. Itse asensin VLC:n, mikä on ilmainen open-source multimedia playeri, jolla voi katsoa melkein minkä tahansa formaatin videoita. Esim windowssin oletus media player ei välillä suostu tiettyjä video codecceja avaamaan, ja tällöin varmaan helpointa on vaan avata se VLC:llä. Toinen ohjelma minkä asensin on "Terminator". Se on Linuxille tarkoitettu Terminal-emulator, jonka avulla voit pitää useaa terminaalia auki samanaikaisesti, ja vaikka tehdä custom keybindit, millä pystyt vaihtamaan suoraan yhdestä terminaali-ikkunasta toiseen. (kuva alempana) Kolmas ohjelma minkä asensin oli Audacity, joka on hyvin tunnettu audio-editori. Asensin nämä kaikki 3 samaan aikaan siis komennolla "sudo apt-get install vlc terminator audacity" ---Testasin myös, ja kaikki 3 ohjelmaa toimii kuten pitääkin.


![Alt Text](images/Image3Softwares.png)

Latasin myös tuon python packet managerin (pip3) ja koitin ladata alkuun "https://steemit.com/linux/@netscape101/download-music-to-mp3-with-the-command-line-in-linux" -ohjeiden mukaan sellaisen ohjelman kuin youtube-dl (joka periaatteessa vaan lataa youtubesta URL:n avulla videon ja converttaa sen .mp3 tiedostoksi, jota voi sitten kuunnella lokaalisti koneelta, mutta jostain syystä tuo komento "sudo pip3 install youtube-dl" ei onnistunut, ja ongelma vaikutti sen verran monimutkaselta varsinkin tälläisen aloittelevan Linux-käyttäjän silmään, että päätin vaan ottaa easy-routen ja käyttää netissä olevaa YT URL to mp3 file converteria, jossa kesti alle minuutti. 

# c) tehtävä --- Tärkeimmät hakemistot

kuten "https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited" -sivulla mainitaan, Linuxissa ei ole erillisiä levyjä kuten windowssissa esim C:// D:// jne, vaan kaikki asennetaan rootin alle. Sinun tarvitsee muistaa vain muutamat tärkeät directoryt, jotka ovat: / ---tämä on Root, eli kaikista ylin directory, minkä alle kaikki muu asentuu. Sitten sen alapuolella on /home, johon tallentuu kaikki eri käyttäjät esim omassa tapuksessani /home/pasis/. Toinen tärkeä on /etc/, täältä löytyy kaikki järjestelmän asetukset luettavissa tekstitiedostoissa. Neljäs tärkeä directory on /media/, se on tarkoitettu esim ulkoisille muistitikuille. Eli jos tökkäät USB-muistitikun niin se tallentaa sen /media/ directoryyn. (lähde: https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/#:~:text=The%20%2Fmedia%20directory%20contains%20subdirectories,the%20CD%20inside%20this%20directory.) <br>
Ja vielä yksi tärkeä hakemisto on /var/log/, joka sisältää järjestelmän erilaisia logeja, joita voi katsella.

Ensiksi kävin katsomassa /etc directoryä, ja avasin locale.conf tiedoston

![Alt Text](images/LessImage2.png)
![Alt Text](images/lessImage1.png)
<br>
Sitten kävin /home/pasis/ hakemistossa ja kävin katsomassa mitä /downloads/ kansiosta löytyy, ja sieltä löytyi aikaisemmin ladattu .mp3 tiedosto

![Alt Text](images/LessImage3.png)

Sitten kävin katsomassa /var/cache/man/fi sisältä ja sieltä löytyi tälläinen

![Alt Text](images/LessImage5.png)
![Alt Text](images/LessImage4.png)

# d) ja e) tehtävät --- Grep ja Pipes

Latasin sample.txt tiedoston netistä, ja testasin grep-komentoa sillä 

![Alt Text](images/Grep1.png)

Sen jälkeen testasin putkia, käytin komentoa sudo journalctl | grep --color -i "X86" ----sudo journalctl tuo esiin system logeja, ja tuo grep komento putkituksen avulla etsii sieltä sisältä kaikki kohdat missä on "X86", ja tuo --color värittää ne, ja -i komento vaan meinaa, että tulokset eivät ole case-sensitive, koska tuolla logeissa ne kaikki lukee pienellä x:llä (x86). (lähde: https://www.digitalocean.com/community/tutorials/grep-command-in-linux-unix)

![Alt Text](images/Grep2.png)


# f) tehtävä (lshw)

lshw:n asennettua käytin komentoa sudo lshw -short -sanitize, ja se listasi tekstimuodossa virtuaalikoneeni specsit,


![Alt Text](images/Grep3.png)

Toi on vaan siis vähän sama kun katsoisi Host koneelta esim HWinfo-softalla mitä kaikkea rautaa sun koneesta löytyy, mutta nyt kun ollaan tekemisissä virtuaalikoneen sisällä, niin tuo komento näyttää sen virtuaalikoneen specsit. Prosessori näkyy tuolla suht. ylhäällä ja system memory näyttää 8064MB, koska allokoin host-koneeltani virtualboxissa 8GB RAM-muistia virtuaalikoneelle.







# Lähteet
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
https://dev.to/xeroxism/how-to-install-terminator-a-linux-terminal-emulator-on-steroids-1m3h   (täältä löysin Terminator-ohjelman)
https://steemit.com/linux/@netscape101/download-music-to-mp3-with-the-command-line-in-linux <br>
https://terokarvinen.com/linux-palvelimet/#h2-komentaja-pingviini <br>
https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/#:~:text=The%20%2Fmedia%20directory%20contains%20subdirectories,the%20CD%20inside%20this%20directory. <br>
https://www.digitalocean.com/community/tutorials/grep-command-in-linux-unix <br>
https://www.geeksforgeeks.org/lshw-command-in-linux-with-examples/
