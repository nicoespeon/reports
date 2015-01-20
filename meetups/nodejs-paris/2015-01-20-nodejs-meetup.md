# Node.js Paris - 20/01/15 (FR)

## Gestion d'erreurs en node.js

### Classiquement, throw

Mécanisme de base : utiliser `throw` combiné avec un `try/catch` pour récupérer ça proprement.

### Le monde asynchrone

Avec node.js, la convention c'est de passer `err` en premier paramètre d'une fonction. Dans l'idéal, on évite le multiple arguments donc on utilise un objet du genre : `function( err, res ) {}`

On a également les promesses pour catch les erreurs.

Également en node : les **EventEmitter**. On crée un nouvel emitteur, avec un listener (sinon node.js crash), puis on peut émettre une erreur.

### Hériter Error

Pour distinguer les erreurs entre elles, les regrouper et simplifier le retour des erreurs dans la console.

L'idée c'est donc d'hériter Error pour récupérer la stack trace.

### Unifier le rendu

Quelques subtilités lors de l'héritage, il faut contourner des soucis de compatibilité pour capturer la stack trace, puis des subtilités de JS pour éviter les boucles infinies =)

Ensuite, on fait sauter les subtilités de `Error.prototype.inspect` qui change le rendu en fonction du type (des `[]` autour des fonctions & cie).

### La suite ?

L'idée serait d'optimiser un peu le tout :

- `err.stack` pèse lourd, trop lourd
- ajout de sémantique sur les erreurs
- internationaliser les erreurs
- avoir des assertions pratiques
- etc.

Du coup, l'intervenant à développé un package npm : [`err-tree`](https://www.npmjs.com/package/err-tree).

Actuellement, ça *beautifie* le rendu des erreurs avec des options pour configurer le retour. On peut même l'appliquer sur l'ensemble des erreurs JS classiques.

On peut également faire des assertions pratiques du genre : `MyError.assert( condition, "It failed" )`.

Enfin, on peut également accéder à la stack trace en JS… aussi =)

## Glou : un système de pipeline compatible avec Gulp

### Rappel sur les streams

Cf. le talk de Florent Jaby "Les streams en node.js".

Généralement, on pipe les streams (comme en UNIX). C'est le principe sur lequel se base Gulp (par rapport à Grunt, qui se base sur de la configuration).

*Note: en node.js, on peut faire passer des objets dans les streams.*

Pourquoi utiliser les streams ?

- pour faire du parrallélisme - on // les opérations
- écriture disque seulement quand c'est nécessaire, pas toujours
- données chargées en RAM uniquement quand c'est nécessaire

Autrement dit : c'est plus robuste / scalable / rapide.
De plus, on gère des streams donc tous les principes du *Reactive Programming* s'appliquent (également du *Functional Programming*… et donc du FRP).

### Pourquoi Gulp c'est quand même chiant ?

- pas de routines
- pas de gestion d'erreur… pas pratique avec JSHint (quand simple warning)
- builds incrémentaux complexes à réaliser… puisque il rejoue tout le build à chaque update

Le Gulpfile devient donc rapidement dur à maintenir.

### Nécessité d'un duplexer

L'idée, c'est de permettre l'extraction d'une portion de la pipeline dans une variable. Ainsi, on va pouvoir composer les opérations.

Le duplexer, c'est la notion qui permet de faire ça.

Il y a `multipipe` qui permet de faire ça justement, mais il utilise des vieux streams de node v0.8. De plus, on a un problème : on a le même nom de destination + les fichiers sont écrits avec le même contenu.

### Les streams sont des EventEmitters

On peut gérer les erreurs sur les stream, avec `.on('error', errCb)` ! Mais ça devient vite ingérable (il y en a partout).

Solution : ré-emit toutes les erreurs.

Mais dans l'ensemble, `multipipe` ne gère pas un certain nombre de cas et de problématiques. Ce n'est pas la solution idéale pour faire tout ça proprement…

### Du coup, il a fait glou !

[Glou](https://www.npmjs.com/package/glou) gère ce qu'on veut faire exactement. Il suffit d'utiliser `glou` plutôt que `gulp`.

## Les domaines en node (v2)

Gestion des erreurs en node.js -> on perd souvent le contexte et la stack trace ne nous aide pas. Sur des erreurs qui arrivent dans des cas en prod (souvent), c'est pas très pratique pour debug.

Un truc qui permet de palier à ça (bien que ça impacte les perfs, ça marche tout de même en début de projet) : `longjohn`.

La perte de contexte d'une erreur (déclenchée depuis un `setTimeout` par exemple) est dû au mode de fonctionnement de node et de ses event loops : il "reprend la main" à chaque exécution de fonction. Quand le timeout est exécuté, node a "oublié" qui l'avait lancé. C'est ce qui fait la force du I/O de node.js.

Du coup, l'idée serait de taguer les tâches à l'intérieurs de notre event loop pour remonter au "flow d'exécution" : c'est ce qu'on appelle les **domaines**.

L'API est actuellement encore instable, mais dans node `v0.8.0` ça marche bien. Il s'agit du package npm `domain`.

Les domaines permettent de ré-introduire une méthodologie de résolution de bug : quand un problème se produit, on est capable de savoir quoi `catch` plus tard et gérer ce qu'il se passe "dans ce cas là".

Principal usage des domaines : l'introduire dans un middleware. Quand une requête est créée, on lui associe un domaine. Du coup quand une erreur "pop", elle est tagguée \o/

### Quelques caveats

Avec MySQL : la réponse n'est pas dans le même domaine que celui qui a lancé la requête. Cela vient du fait de la nature séquentielle MySQL notamment (mise en attente du requête). On peut forcer le domaine en le bindant cela dit. Use NoSQL (if relevant for your business) ;-)

### Bien plus qu'une gestion d'erreurs

Les instances node qui durent longtemps = on ne veut pas de leak. Du coup, on détruit les objets. Mais les objets ont des dépendances (éventuellement cycliques).
