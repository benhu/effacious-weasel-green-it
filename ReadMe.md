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
Cette mesure est la moins précise des trois, car c'est un applicatif qui mesure la consommation du port USB et non la consommation totale du Raspberry. On récupère l'intensité utilisée par le port USB en ampère, ainsi sachant que la tension d'un port usb est en moyenne de 5 volt, il est possible d'en déduire la consommation en Watts. Le matériel necessaire est donc très minime mais la précision est réduite. L'avantage est donc de logger très facilement les résultats.

#### Mesurer avec un testeur/enregistreur de port USB
Un testeur de port USB ce présente comme une clé usb mais qui offre la possibilité de connecter un autre péripherique usb.
![Testeur avec écran](https://github.com/benhu/effacious-weasel-green-it/raw/master/testeur_usb.jpg)
Ce genre d'outils coute peu cher (6 euros sur Amazon), la récupération d'information de consommation est relativement peu aisée, dans la mesure où l'outil ne propose pas nativement la récupération sur un ordinateur, cependant il affiche l'intensité, la tension ainsi que la consoommation du périphérique connecté. Ce genre de testeur peux-être réalisé soit-même grâce a un arduino, dans ce cas là on alimente le raspberry via le GPIO (pin 2 et 6) en utilisant l'arduino et on récupère l'information de consommation via l'arduino. Ce moyen possède un cout cependat plus élevé.

#### Mesurer sur les pins de la raspberry avec un multimètre (via les pins 2 et 6)
Pour mesurer la consommation, il est possible de mesurer l'intensité au sein du raspberry. Cependant ne pourrons être loggées dans un outil informatique. Pour cet montage il est necessaire de faire l'acquisition d'un multimètre (12 euros sur amazon).
![Schéma](https://github.com/benhu/effacious-weasel-green-it/raw/master/schema.png)
Il possible d'utiliser un oscilloscope numérique afin d'obtenir les données directement sur informatique.

### De manière indirecte :
#### Utiliser PowerTop (powertop --html)
 * Matériel nécessaire : Un PC sous Linux, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep sur le fichier html généré
 
#### Utiliser perf
 * Matériel nécessaire : Un PC sous Linux, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep

#### Script pour mesurer la performance et la consommation [Power and performance measurement](http://raspi.tv/2015/raspberry-pi2-power-and-performance-measurement)
 * Matériel nécessaire : Un PC sous Linux avec python, un cable USB
 * Investissement : Matériel déjà en possession
 * Récupérer le résultat : de manière automatique avec une commande grep
