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
Powertop mesure la consommation sur le pc complet, cela comprend donc les ports usb. Ce moyen est donc relativement imprécis. Pour récupérer les résultats, il n'est pas possible d'interragir facilement avec powertop pour récupérer les données de consommation. Pour cela il faut générer une page html (via `powertop --html`) et ainsi via `grep` récupérer la consommation du port usb. Cet outils affiche directement la puissance du raspberry. Cette méthode peux être exécutée depuis le raspberry et ainsi on obtient la puissance extimée du raspberry. Une autre commande peut-être utilisée afin d'obtenir la puissance du raspberry, il s'agit de la commande `perf`.


#### Script pour mesurer la performance et la consommation
Il est possible de récupérer la puissance consommé ainsi que la performance du raspberry directement depuis celui-ci. Cette methode est un script python :
```
#!/usr/bin/env python2.7
import time
from subprocess import call
from threading import Thread
 
cmd = "python /home/pi/presort.py"
 
def process_thread(i):
    print "Thread: %d" % i
    start_time = time.time()
    call ([cmd], shell=True)
    end_time = time.time()
    elapsed_time = end_time - start_time
    print "Thread %s took %.2f seconds" % (i, elapsed_time)
 
how_many = int(raw_input("How many threads?\n>"))
 
for i in range(how_many):
    t = Thread(target=process_thread, args=(i,))
    t.start()
```
Cette méthode est donc similaire à l'utilisation de powertop dans le raspberry et offre, en plus, l'avantage de ne pas avoir a parser un fichier html pour obtenir la puissance du raspberry.

## Choix de la solution
Afin de mesurer la consommation de manière précise, il est préférable d'utiliser la solution avec l'Arduino pour mesurer et alimenter le Raspberry. Cette solution présente l'avantage d'être facilement récupérable de manière numérique et ainsi être en mesure d'être analysable facilement. De manière indirecte la meilleurs solution reste le script python, car il s'agit d'un script, donc facilement modifiable et ainsi être capable d'envoyer ou de stocker les données dans un système adapté.
