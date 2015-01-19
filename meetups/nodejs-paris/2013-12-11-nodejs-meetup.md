# Node.js Paris - 11/12/13 (FR)

## Les promesses via `deferred.js`

La promesse représente une valeur future (cf. analogie avec le pêcheur et son fils).
Le structure est plus proche du synchrone.

En `node.js` on utilise `deferred.js`. Implémentation bien optimisée, avec des helpers pratiques (`each()`, `map()`, etc.).

`promisify()` prend une fonction asynchrone (un `callback()`) et optionellement le nombre d'arguments. Puis il retourne une fonction qui renvoie des promesses plutôt que de prendre des callbacks. On l'a *promessifiée* !

`synchronize()` permet d'être sûr que toutes les promesses sont résolues avant de poursuivre.

Un autre référence du domaine, c'est `Q`. La syntaxe diffère et, cela étant, il est moins performant (quand même).


## node.js et Windows Azure

Il y a un *developer helper* dédié à **node.js** intégré à Windows Azure, avec des liens vers les fonctions cloud de Microsoft.

Azure fait du PaaS, il est capable de rendre facilement scalable des instances qui tournent sur node.js.

Bon en gros, c'est plutôt propre. Ils intègrent complètement leurs services de A à Z avec ouverture vers les autres solutions (dépôt git standard, node module `azure-cli` pour gérer ça en ligne de commande, etc.).

Par contre ils se font poutrés par Amazon niveau matos pour le cloud.

**N.B : Actuellement c'est encore une alpha...**


## `ExoBrowser` et `Breach`

Il s'agit de faire tourner un navigateur, codé en **JavaScript**.

L'idée de départ vient du fait de vouloir normaliser le comportement du navigateur, par le biais du JS. Cela devrait permettre de résoudre un certain nombre de soucis tels que :

- la multitude de tabs qui s'accumulent
- la synchronisation des cookies et du localstorage pour pouvoir y accéder de n'importe où (on se log dans son browser)
- et aussi parce-que c'est stylé

L'idée est donc de créer une plateforme complètement modulaire, écrite en JavaScript. C'est un peu la même vision de départ de Firefox.

`Breach` est l'API qui vient faire communiquer les modules (que l'on peut développer et proposer sur GitHub), avec `ExoBrowser`.

Liens :

- <http://breach.cc>
- <https://github.com/breach/breach_core>

**N.B : Au final, c'est du très très groskiki pour permettre aux devs de configurer/coder LEUR navigateur**


## S.A.R.A.H : les objets connectés

**S.A.R.A.H = Self Actuated Residential Automated Habitat**

C'est un framework open-source qui permet d'intéragir avec l'internet des objets.

Plus ça va, plus les constructeurs sont amenés à rencontre les éditeurs. Du coup le hardware et le software se rejoignent avec une homogénéisation des interfaces, des APIs.

Désormais, avec la Raspberry Pi, l'imprimante 3D et le crowdfunding permettent de créer plein d'entreprises qui se focalisent sur certaines fonctionnalités, dans certaines directions.

L'idée, c'est donc de pouvoir faire communiquer toutes ces fonctionnalités.
**S.A.R.A.H** va faire communiquer tout le monde via les requêtes HTTP. On normalise tout ce qui est déjà du HTTP avec le CRON (comme GMail), le scraping (objets virtuels, crawler un site web) et le custom (ceux qui font le truc à leur sauce).

Techniquement, il faut aussi pouvoir disposer d'une interface pour ne pas avoir à sortir des trucs g33ks dégueulasses (genre la console) pour allumer sa lampe ! Une interface tactile (tablette), voire vocale, pour faire communiquer sa domotique… On se prend un peu pour Tony Stark.

On a donc des plugins qui permettent d'interfacer S.A.R.A.H avec différents medium :

- vocal
- QRCode
- XML gestures (visuel)
- facial recognition (openCV)

C'est rien que de la requête HTTP !

Avec **IFTTT** on peut plug des services différents, en ligne. Utilisé dans S.A.R.A.H, on va chaîner les plugins. On peut donc demander vocalement d'envoyer un mail derrière ou d'avoir des notifs par d'autre medium que le vocal (par exemple).

De plus, plutôt que de développer en dur, on peut développer de l'intelligence artificielle pour adapter le comportement de S.A.R.A.H avec les habitudes de l'utilisateur, tout en permettant de faire une correction vocale derrière.

**N.B : Éventuelles alternatives intéressantes à consulter > Ninja Sphere, SmartThings, Mother**
**N.B bis : Jeter un oeil à IFTTT**
