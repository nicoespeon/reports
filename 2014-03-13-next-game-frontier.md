# Next Game Frontier - 13/03/14 (FR)

Note : cette conf sur le jeu vidéo HTML5 est très orientée "jeu vidéo 3D" (et donc utilisation de canvas). On s'écarte pas vraiment des sentiers battus, ce qui est dommage même si c'est sympa.

## Create a 3D game with WebGL and Babylon.js (David Rousset)

WebGL = API bas niveau.

On utilise plutôt un moteur (genre **Three.js** et **babylon.js**) pour ne pas avoir à gérer toute la complexité.

David présente essentiellement son moteur de jeu 3D et les éditeurs qu'ils ont construit autour : assez impressionnant pour créer rapidement des scènes 3D complètes en HTML5. C'est également ultra-performant. Ca utilise les `<canvas>` (of course).

C'est open-source : https://github.com/BabylonJS/Babylon.js

Ca fonctionne également sur mobile avec les gestures (et c'est plutôt sexy).

**IndexedDB** est une API de stockage côté client qui permet de gérer des quantités importantes de données structurées et des recherches de haute performance sur ces données en utilisant des index.

## The Web as a platform for games - from WebGL to asm.js (Nicolas Silva)

Difficulté actuelle travailler sur de nombreux écosystèmes qui bougent. Il faut des skills différentes sur chaque plateforme si on fait du natif.

En 2014, on doit encore "installer" des jeux pour les essayer...

Si on veut faire un jeu, et non pas un jeu pour une plateforme, alors on va travailler en HTML5.

Présentation de [asm.js](http://www.asmjs.org), propulsé par Mozilla. C'est un sous-ensemble de JavaScript qui se compile en C/C++ avant l'exécution pour atteindre les performances du natif. Par contre, c'est encore dans les cartons à l'heure actuelle.

Petit bémol : Nicolas insiste pas mal sur les avantages de ne pas avoir à download un jeu... le soucis c'est que du coup c'est tout online et que si t'es pas connecté, beh tu peux pas jouer. Et pour illustrer -> il n'a pas réussi à nous faire des démos parce-qu'il n'avait pas de réseau.

##  Create 3D assets for the mobile world & the web, the point of view of a 3D designer (Michel Rousseau)

Gros problèmes de performance sur mobile... il faut pouvoir s'adapter pour y développer des jeux.

Les points à considérer :

- réduire la taille des textures... de manière intelligente (réduire la pollution, ne pas inclure ce que le moteur de jeu ne gère pas)
- optimiser les matériau
- etc. (pleins de points graphiques 3Ds un peu poussés, faut maîtriser ses outils quoi)

## Enhancing HTML5 gaming using WebCL (Swaroop Kalasapur & Satheesh Sudarsan)

**WebCL** permet de booster les calculs de rendering JavaScript par-dessus **WebGL**.

C'est encore en early stage actuellement. Open source et propulé par Samsung.

## Three.js (Jerome Etienne)

Framework JS pour rendu de jeu 3D.

## Minko.io (Jean-Marc Le Roux)

Framework JS pour rendu de jeu 3D, basé sur **asm.js**.
