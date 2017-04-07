# Notes réseaux et mémos

---
## Cours
* Mettre étapes d'une connexion internet
* Protocol IP couche 3
* modele OSI 7 couches | modele TCP/IP 4 couches ![osi]

|    #   | Modèle OSI           | Modèle TCP/IP  | Rôle et Exemple | Protcl
| ------------- |:--------:|:-----:|:------:|:----:|
| 7     | Application | Application | internet |X|
| 6    | Présentation     |   Application| |X|
| 5 | Session      |    Application | |X|
| 4 | Transport      |    Transport| connexion de processus a processus, controle de flux .firewall| TCP/UDP|
| 3 | Réseau     |    Réseau | interconnexion de reseau via routage. routeur/gateway| ARP,IPv4/6|
| 2 | Liaison de données      |    Liaison  de données | switch|ethernet|
| 1 | Physique      |    Physique| prise RJ45 hub |X|

* hub = communique en broadcast (couche 1)
* switch = communique avec l'adresse direct de la machine (couche 2)
* Câble ethernet : 4 paires torsadées - 1 pour envoyer 1 pour recevoir et 2 qui servent a rien

|En Octets |
|-------
|0|1|2|3|4|5|6|7|8|9|10|11|12|13|14 ... 1513|1514|1515|1516|1517|
|-|-|-|Adresse MAC de destination|-|-|Adresse MAC Source |-|-|-|-|-| Type protocol |-|Données| FCS/CRC|-|-|-|
1. Donc : trame (frame) ethernet
 * adresse destination  	6octets (48bits)
 * adresse source       	6octets (48bits)
 * Type			2octets (16bits)
 * Données 		46 octets (min) - 1500 octets (max)
 * Checksum 		4 octets (32bits) en CRC


* Adresse de réseau `00:00:00:00:00:00 ` sur 6 octets
* Adresse broadcast `FF:FF:FF:FF:FF:FF` sur 6 octets

[osi]: https://upload.wikimedia.org/wikipedia/commons/7/7e/Comparaison_des_mod%C3%A8les_OSI_et_TCP_IP.png "Schema osi et tcp/ip"

---
## Pratiques
* Si host unreachable -> check le routage avec `route` ou `route -n`
>Pour ajouter une route `route add  default gw 192.168.1.0 netmask 0.0.0.0`

* Pour voir tous les ports en ecoute udp `netstat -anpu`
* Pour voir tous les ports en ecoute TCP `netstat -antp`
* `/etc/resolv.conf` conf DNS
* Quand on se branche en ethernet l'un a l'autre :  `sudo ifconfig eth0 192.168.10.2 netmask 255.255.255.0` et l'autre : 	`sudo ifconfig eth0 192.168.10.3 netmask 255.255.255.0`
---
## Système
* `iptables -L` liste les parefeu et gere port forwarding
* `/etc/passwd` utilisateur du système
* Pour changer adresse ip `ifconfig {interface} 192.168.0.0`
* `passwd` pour changer le mot de passe de l'utilisateur actuel
* `find / -name nom_du_fichier` pour chercher partout via le nom_du_fichier ou `locate nom_du_fichier` mais il faut que la bdd de locate sois maj
* Vérifier qu'un fichier est installé (ubuntu/debian) `dpkg -l | grep nom_du_fichier`
* `sudo -s `ou `sudo su` pour etre ultra admin
* Eteindre l'ordi dans 13 minutes (-h now pour arreter direct) `shutdown -h + 13`
* `ALT+clic` droit pour supprimer un lanceur dans la barre de tâche de Gnome 3 version classique.
* installer un .deb  `sudo dpkg -i *.deb`
* pour voir tous les processus : `top` ou `ps -aux` ou le mieux utilisé `htop`
* rendre un fichier éxécutable  `(sudo) chmod +x <nom_du_fichier>`
* refresh réseau `sudo /etc/init.d/network-manager restart`
* refresh bluetooth `sudo /etc/init.d/bluetooth restart`
* télécharger vidéo `youtube-dl (pour avoir que le son -x) lien_de_la_vidéo.html`
* Supprimer un dossier rempli `rm -r directory` ou `rm -Rf dossier`
* Identifier et fermer un programme : `ps aux | grep -i “name of your desired program”` &
`sudo kill -9 process_id `
* Connaitre sa version de linux : `lsb_release -a` et `uname -r` pour le kernel
* installer un .run `sudo sh nomdufichier.run`
* ajouter un ppa `sudo add-apt-repository ppa:<nom_du_dépôt>`
* connaitre sa Carte Graphique: `lspci | grep VGA`
* Comparer deux fichiers : `sdiff premierfichier autrefichier (|more en option)`
* pour savoir dernier edit d'un fichier `ls -rtl`
* Regarder l'espace dispo: `free -m`
* Sauvegarder les images d'un PDF: `pdfimages -j urfile.pdf debut_nom_image_enregistree`
* Trouver les plus gros fichiers de votre disque dur :(remplacer /home/manu par ce qu'on veut)
`du -hms /home/manu/* | sort -nr | head`
* Pour retrouver dernière commande via debut de son nom `Echap + p + début du nom de la commande`
* Chemin du dossier personnel de l'utilisateur peut etre remplacé par ~
* voir son ip externe `wget -O - -q icanhazip.com `
* Syst (aussi nommée « SysRq » sur certains clavier) est en fait celle de l'impression d'écran : « Impr. écran », « Print screen » ou autre. Elle est généralement située en haut à droite du clavier.
1. Raccourcis :
  * Synchronisation des disques 		`Alt–Syst–s`
  * Stoppe les programmes gentiment 	`Alt–Syst–e`
  * Tue tous les programmes 		`Alt–Syst–i`
  * Disque principal en lecture seule 	`Alt–Syst–u`
  * Redémarrage brutal de l'ordinateur 	`Alt–Syst–b`
  * Arrêt brutal de l'ordinateur 		`Alt–Syst–o `

---
## Mémo git
Se servir de git quand projet fait
1. (`git pull`) pour récupérer ce qu'il y a sur le serveur
* `git add (vos fichier ou alors .)`
* `git commit -m 'je viens d'uplaod ça'`
* `git push`

Initialiser un projet
1. `echo "# projects" >> README.md`
* `git init`
* `git add README.md`
* `git commit -m "first commit"`
* `git remote add origin https://github.com/kasuke5/projects.git`
* `git push -u origin master`
---
## Mémo sublim text

* `Ctrl + Shift + é` Place en commentaire (/\* \*/) les lignes sélectionnées
* `Ctrl + é` Place en commentaire (//) les lignes sélectionnées
* `Alt + F3` Si on place le curseur sur une variable, par exemple, et que l'on veut modifier son nom, Alt + F3 nous permettra de modifier toutes les occurences de cette variable en même temps (multiple - editing)
* `Alt + Shift + 2 (ou 3, ou 4)` Séparer Sublime Text en 2 colonnes. Pratique pour modifier deux fichiers en même temps.
* `Ctrl + Shift + D` Duplique la ligne du dessus

Pour le développement Web
* `Écrire : html, ensuite TAB` Ceci va créer un template HTML5 complet!
* Il est aussi possbible d'écrire directement une balise avec un id ou une classe. Il ne faut aucun plugin c'est natif à sublime text 3. Il suffit d'écrire : `balise.nomclass+tab` Cela produira une balise ayant comme classe la classe donnée.
Dans le même ordre d'idée il est possible de déclarer un id :
`balise#nomid + tab`
---
## Mémo VIM

* rechercher un élément : -> `?`
* `/ `	Rechercher du texte
  * `n `	Rechercher l'occurence suivante
  * `N `	Rechercher l'occurence précédente
* `CTRL + r `-> l'inverse de `CTRL-Z `
* `u` -> Ctrl-Z maggle
* `dd` -> couper toute la ligne
* `Y` -> copier toute la ligne
* `x` -> supprimer un caractÃ¨re
* `o` -> mode insertion en dessous
* `O `-> mode insertion au dessus
* `r` -> remplace qu'un seul car.
* `R` -> remplacer un cara. et activer mode insertion
* `i` -> mode insertion
* `p`-> coller
* `cw` -> changer un mot
* `$` -> aller a la fin de la phrase
* `.` -> refaire l'action précédente
* `dw` -> supprimer un mot
* `~` -> mettre en maj sur caractère
* `:%s/lemot/remplacelemot/g `-> (pour plusieurs sur une ligne) -> remplace tous les "lemot" par "remplacelemot
* `:set ai || :set noai `-> active ou non l'auto indentation
* savoir dans quel fichier on est `CTRL+G`
* ranger bien un json_pp -> `:%!json_pp`
* hors vim, copier le contenue d'un fichier dans un autre cp 1erficher.js 2efichier.js

---
## Se connecter à hugo
`smb://hugo.etd-p.esiea.fr/pub/`
---
## Mémo Wireshark

* `ip.src==adresse `: filtrer les adresses source
* `ip.dst==adresse `: filtrer adresse de destination
