Rapport de Green IT
==

# Objectifs

* Mesure/Facturation de la consommation énergétique (matériel, installation, investissement)
 * Direct
 * Indirect
* Expérimentation (faire un schéma)
 * Prototype/protocole
 * Raspberry (ARM)

Mesure de consommation électrique, comment on fait ? Quel cas ? directe ? indirecte ?
Comment on mesure, qu’est ce que l’on mesure ?


## Comment mesure-t-on la consommation électrique d'un Raspberry ?
* De manière directe :
  * Mesurer la consommation du port USB lorsqu'il est branché via la commande usb-devices
  * Mesurer avec un testeur/enregistreur de port USB [Testeur avec écran](http://www.framboise314.fr/jai-teste-pour-vous-un-testeur-de-port-usb/)
  * Mesurer sur les pins de la raspberry avec un oscilloscope (via les ports 2 et 6) :
  ![Schéma](https://raw.githubusercontent.com/benhu/effacious-weasel-green-it/master/sch%C3%A9ma.PNG)

* De manière indirecte :
  * Utiliser PowerTop (powertop --html)
  * Utiliser perf
  * Script pour mesurer la performance et la consommation [Power and performance measurement](http://raspi.tv/2015/raspberry-pi2-power-and-performance-measurement)
