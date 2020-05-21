# plugin-husqvarna

**Installation**
* Télécharger le plugin depuis Github. Je vous suggère de télécharger les versions avec tags ("husq_vx.y")
* Si vous avez déjà le plugin husqvarna installé sur votre jeedom, vous pouvez supprimer l'équipement jeedom correspondant, et faire une  sauvegarde par précaution du dossier correspondant dans le répertoire plugin de jeedom.
* Dézipper la nouvelle version du plugin dans le dossier plugin de jeedom (le même nom husqvarna est utilisé)
* Aller dans le menu "plugins/objets connectés/Husqvarna" pour installer le nouveau plugin.
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
