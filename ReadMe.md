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
### De manière directe :
#### Mesurer la consommation du port USB lorsqu'il est branché via la commande usb-devices sur le pc qui alimente le rasp.
 * Cette mesure est la moins précise des trois, car c'est un applicatif qui mesure la consommation du port USB et non la consommation totale du Raspberry. 
 * Matériel nécessaire : Un PC sous Linux, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep :
 
  * Les deux suivantes ont une marge d'erreur peu importe et équivalente car la mesure est réalisée par un outil spécialisé.
   * Mesurer avec un testeur/enregistreur de port USB ![Testeur avec écran](https://github.com/benhu/effacious-weasel-green-it/raw/master/testeur_usb.jpg)
 * Matériel nécessaire : Le testeur USB, une alimentation pour le Raspberry, un câble USB
 * Investissement : 6 euros pour le testeur
 * Récupérer le résultat : Noter à la main les résultats
   * Mesurer sur les pins de la raspberry avec un multimètre (via les pins 2 et 6) :
  ![Schéma](https://github.com/benhu/effacious-weasel-green-it/raw/master/schema.png)
 * Matériel nécessaire : Un multimètre, une alimentation, un câble USB
 * Investissement : 12 euros pour le multimètre
 * Récupérer le résultat : Noter à la main les résultats

### De manière indirecte :
#### Utiliser PowerTop (powertop --html)
 * Matériel nécessaire : Un PC sous Linux, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep
#### Utiliser perf
 * Matériel nécessaire : Un PC sous Linux, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep
#### Script pour mesurer la performance et la consommation [Power and performance measurement](http://raspi.tv/2015/raspberry-pi2-power-and-performance-measurement)
 * Matériel nécessaire : Un PC sous Linux avec python, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep
