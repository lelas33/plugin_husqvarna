# plugin-husqvarna

**Fonctions**

Ce plugin est basé sur la version de référence disponible sur le market Jeedom, et ajoute des fonctions complémentaires.
Il reste globalement compatible de cette version de référence, car les Infos et Commandes existantes ont été conservées.

Les fonctions ajoutées au plugin actuel sont:
* La position courante GPS du robot et des 50 dernières positions pour l’affichage sur une carte dans le widget.
* La gestion d’une planification du robot sur un rythme hebdomadaire, avec 2 plages horaires quotidiennes, et la possibilité de sélectionner une zone active du robot par commande Jeedom (pour ceux qui ont mis en place 2 zones de tontes avec commutation par relais)
* La possibilité d’interrompre et de reprendre la planification en fonction de la météo, par couplage avec le plugin «Vigilence Météo / pluie à 1 h».
* La mise en place d’une page «panel» qui permet:
  * D’afficher sur une carte les positions du robot dans le temps. Cela permet de visualiser si le robot couvre uniformément l’espace à tondre.
  * D’afficher la configuration actuelle du robot (juste pour information pour le moment)

<p align="left">
  <img src="../master/doc/images/widget.png" width="300" title="Widget dashboard">
</p>

**Installation**
* Télécharger le plugin depuis Github. Je vous suggère de télécharger les versions avec tags ("husq_vx.y")
* Si vous avez déjà le plugin husqvarna installé sur votre jeedom, vous pouvez supprimer l'équipement jeedom correspondant, et faire une  sauvegarde par précaution du dossier correspondant dans le répertoire plugin de jeedom.
* Dézipper la nouvelle version du plugin dans le dossier plugin de jeedom (le même nom husqvarna est utilisé)
* Aller dans le menu "plugins/objets connectés/Husqvarna" de jeedom pour installer le nouveau plugin.
Sur la page configuration du plugin, vérifier vos identifiants de login sur les serveurs Husqvarna, et cochez la case :"Afficher le panneau desktop". Cela donne accès à la page du "panel" de l'équipement.

**Configuration**
Une fois l'installation effectuée, lancer la détection de votre robot, ce qui crée l'équipement correspondant.
* Sur l'onglet "**Equipement**", choisissez l'objet parent
* Sur l'onglet "**Config.Carte**", vous pouvez définir l'image qui sera utilisée par le plugin pour l'utilisation de la position GPS de votre robot.
Comme indiqué sur cette page, il faut générer une image au format "png", de taille environ 500 x 500 pixels, qui représente votre terrain et qui soit géo-référencée. Le plus simple pour cela est d'utiliser Google map en mode satellite. (Vous faite une copie d'écran, en notant bien les coordonnées GPS des 2 coins supérieur/gauche et inférieur/droit, sous la forme latitude,longitude (exemple:48.858748, 2.293794)
(Attention, cette carte doit être orientée Nord en haut.)
Le fichier image obtenu doit être placé dans le dossier "ressources" du plugin, sous le nom "maison.png"
* Saisir ensuite les 3 facteurs de taille pour l'affichage respectivement sur les widgets dashboard, widgets mobile, et page panel. (attention, ces champs ne sont pas préremplis par le plugin, il faut les renseigner)
* Saisir ensuite les coordonnées GPS des 2 coins de l'image

<p align="left">
  <img src="../master/doc/images/installation_1.png" width="600" title="Configuration Carte">
</p>

* Sur l'onglet "**Panification**", vous pouvez définir les plages horaires de fonctionnement de votre robot.
Il y a 2 fonctions supplémentaires offerte par la planification du plugin par rapport à la planification intégrée au robot: - La gestion de 2 zones de fonctionnement du robot (voir la description de cette fonction plus bas), et le couplage au plugin "vigilence météo / prévision dans l'heure" pour suspendre la tonte lors de période pluie. (voir également plus bas le détail sur cette fonction)
* Si la fonction "Planification par zones" est utilisée, cocher la case "Gestion de 2 zones", et définissez en utilisant le sélecteur de commandes, les 2 commandes jeedom pour activer chaque zone.
Définissez ensuite le pourcentage de cycle de tonte à réaliser dans la zone 1, le pourcentage de la zone 2 sera bien sur le complément à 100%. (ces ratios sont à priori en rapport avec la surface relative de chaque zone)
* Si l'**option météo** est utilisée, il aut alors renseigner les commandes dans la section "Utilisation de la météo". 
Pour cela, il faut avoir au préalable installé le plugin "Vigilence météo/Pluie à 1h".
En utilisant le sélecteur de commande, indiquer les 2 liens "Pluie prévue dans l'heure" et "Prévision à 0-5 mn".
* Renseigner ensuite la section "Calendrier de fonctionnement".
Il est possible de définir 2 plages horaires par jour, pour chaque jour de la semaine.
(La zone "Initialisation plage horaire 1 ou 2" permet de remplir plus rapidement les informations hebdomadaires en recopiant une même défition sur chaque jour de la semaine).
Pour chaque plage horaire, on peux associer une zone de tonte, avec un chiffre entre 1 et 3:
  * 1: Zone de tonte 1, associée à la commande d'activation zone 1
  * 2: Zone de tonte 2, associée à la commande d'activation zone 2
  * 3: Alternance des zones 1 et 2, selon le pourcentage défini précédemment.
  
<p align="left">
  <img src="../master/doc/images/installation_2.png" width="600" title="Configuration Planification">
</p>
