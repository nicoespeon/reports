# Node.js Paris - 08/01/14 (FR)

Sponsor *à noter* : [Globalis](http://www.globalis-ms.com/) (cherche à travailler avec des devs JS, tout framework confondu)

## Paris Is {API} – The APIness DATA Therapy

- Hashtags : `#makeMeAPI` `#nodejs` `#api`
- GitHub : <http://github.com/ParisNumerique/MakeMeAPI>

Le but c'est de créer des APIs pour les services de la mairie de Paris. Un peu dans une optique d'Open Data finalement.

Quelques liens :

- <http://equipement.paris.fr>
- <http://quefaire.paris.fr>

Les data doivent être **accessibles** et **documentées** :

- directement connectées aux BDD de production
- générer de la doc
- générer des endpoints
- monitorer l'usage

Du coup ils utilisent *MEAN* :

- *M*ongo / yql
- *E*xpress
- *A*ngular
- *N*ode.js

Ses outils sont assez pratiques. Au niveau de ce qui est fat dans la démo, on notera :

- génération automatique de la doc en utilisant **yuidoc** (et c'est cool !)
- utilisation des snippets de ST pour faire une démo de code rapidement

Leur API est générée quasi-automatiquement avec un code intelligemment parsé. En effet, node.js va prendre en compte l'architecture du code (dossier) pour générer les URLs de l'API + la documentation automatiquement. Il suffit de coder le contenu de l'API et tout se met à jour automatiquement (doc + URLs).


## Introduction à Grunt (lol)

Bon c'est une présentation de kesako Grunt à destination des débutants (ceux qui connaissent pas Grunt).

RAS.


## Les addons binaires pour node.js : exemple de libspotify

- GitHub de l'intervenant : <http://github.com/Floby>

### Qu'est-ce-qu'un addon ?

- Un module écrit en C/C++ au lieu de JS.
- Un module node.js compilé.
- Peut invoquer directement des fonctions natives d'autres librairies ou du système.

### Concrètement, ça marche comment ?

C'est une librairie dynamique en `.node` (au lieu de `.do` ou `.dll`).

Node.js charge la librarie avec `dlopen()` lorsqu'on l'appelle avec `require()`. Puis il l'initialise, classiquement.

Pour développer des addons node.js, il faut se mettre à V8 cela dit. En gros, on fait du C.

### ObjectHandle<type> ?

Stocke un pointeur C dans un objet JS, by V8.

### Utilisation depuis JavaScript

Une grosse difficulté quand on développe des addons node, c'est le *multi-threading*. En effet, avec V8 et node.js, **un seul thread est autorisé à accéder à JavaScript**. Du coup, il faut gérer la file d'attente (LIFO, FIFO, etc.).

Un deuxième problème, c'est la compilation (surtout sur W.). Du coup, on utilise un fichier `binding.gyp`.

### Tests

Le code C est minimal et non testé finalement. Le mec utilise surtout `nodeunit` pour tester la partie JS de son code.

### Conseils : KISS

- Mapping le plus minimal JS <-> C/C++
- TDD pour maîtriser la complexité
- Tester l'interface JS
- Utiliser les outils C/C++ que Node.js fournit


## Growing your prototype

Le principe c'est de parler de *Time To Marker* et de MVP. C'est du Lean Management.

### Utilitaires

Valider un document JSON passé en paramètre de Express (API REST) : [paperwork](https://npmjs.org/package/paperwork)
