# Notes réseaux

---
## Cours
* Protocol IP couche 3
* modele OSI 7 couches | modele TCP/IP 4 couches ![osi]
[osi]: https://upload.wikimedia.org/wikipedia/commons/7/7e/Comparaison_des_mod%C3%A8les_OSI_et_TCP_IP.png "Schema osi et tcp/ip"

---
## Pratiques
* Si host unreachable -> check le routage avec `route` ou `route -n`
>Pour ajouter une route `route add  default gw 192.168.1.0 netmask 0.0.0.0`

* Pour voir tous les ports en ecoute udp `netstat -anpu`
* Pour voir tous les ports en ecoute TCP `netstat -antp`
