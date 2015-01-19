# Node.js Paris - 12/02/14 (FR)

## Les enjeux de l'injection de dépendance

Quelques propriétés essentielles :

- unicité du nom -> utiliser des chemins absolus
- capacité de faire un alias -> migration aisée
- capacité d'injecter des prototypes pour les tests (contexte)
- gestion des dépendances récursives -> ordre de déclaration des modules non-détéministe

### Pourquoi require est-il trop limite ?

Require favorise l'utilisation de chemins relatifs... pas glop puisque ça peut dépendre du projet.

Aucun mécanisme pour renommer simplement un module.

Aucun mécanisme par défaut pour injecter des prototypes pour les tests.

La gestion des dépendances récursives marche avec require.js mais est **longue à débuguer**.

**Conseil : n'utiliser que sur des petits projets...**

### Require.js

#### Les bons points de `require.js`

- unicité du nom
- renommage facile
- gestion des dépendances récursives

#### Les mauvais points

- faible sur le besoin test
- asynchronisme sympa en mode client mais lourd côté back-end
- base de code très grosse par rapport à ce que ça apporte
- syntaxe assez laborieuse

**Conseil : utiliser require.js en mode client, pas en back-end.**

### di

Un grand représentant côté back-end est **di**, inspiré de **Angular**.

Plutôt bon d'une manière générale, avec certains bémols :

- ne gère pas le renommage
- gère partiellement le problème de tests
- ne gère pas les dépendances récursives

** Conseil : essayer si ça correspond à notre philosophie.**

### r42 (la solution de l'intervenant)

Il pense avoir résolu toutes les problématiques listées ici. On peut y jeter un oeil [sur npm](https://www.npmjs.org/package/r42).

Fonctionnement de base ->

```javascript
var r42 = require("/path/to/r42.js");

r42
  .config({
    // Configuration happens here.
  })

  // We can chain with deps.
  .inject(deps, function(maps) {
    // Your code should go there...
  });
```

On peut avoir une syntaxe un peu plus légère ->

```javascript
r42.inject(function( , /*!lib/myModule*/ myModule, /*! lib/depA*/ depA) {
  // Your code should go there...
});
```

Les dépendances récursives sont également gérées sans soucis.

On peut loader les modules à la volée ->

```javascript
console.log( "The answer is: " + r42.inject("lib/dynamic") );
```

On peut également utiliser d'autres loaders, du genre JSON ->

```javascript
r42.inject(function( , /*!json!lib/myModule*/ myModuleInJson) {
  // Your code should go there...
});
```

**Note : il sera bientôt utilisé en production à TF1 sur un gros projets avec quelques centaines de fichiers.**

On peut également consulter [la documentation](https://bitbucket.org/qraynaud/r42/overview).


## Ne sous estimez pas npm

On va parler plus exactement du combo :

- npm
- napa
- Browserify

**npm** n'est pas un **node package manager** : il ne se contente pas des projets node, il est simplement optimisé pour les projets node.

Il faut un `package.json` valide pour l'utiliser, contrairement à `Bower`. Pour contourner cette restriction, on peut utiliser **napa** :


```json
{
  "scripts": {
  	"install": "napa"
  },
  "napa": {
  	"foo": "username/repo",
  	"bar": "git@example.com:user/repo"
  }
}
```

De plus, **npm** peut lancer des scripts arbitraires : il peut donc servir de task manager,  à l'instar de **Grunt** ou **Gulp**. Il est bien plus simple, peut appeler n'importe quel type de script MAIS il n'est pas (encore) possible de lui passer des paramètres.

```json
{
	"scripts": {
    	"tests": "grunt tests",
        "foo": "path/to/foo.sh"
    }
}
```

Bonus : tous les packages qui disposent d'une propriété `bin/` sont disponibles. Pas besoin de module global \o/

On peut se servir de **Browserify** pour build son code front-end comme si c'était un code back-end.

```json
{
	"scripts": {
    	"build-js": "browserify src/app.js > build/app.js"
    }
}
```

**Conseil : si on a juste besoin de Grunt / Bower, a priori on a déjà ce qu'il faut rien qu'avec npm et 2/3 petits modules !**
