# Formation au Kanban - 20/11/14 (FR)

## 1. Introduction à Kanban

### Principes

#### Principe 1 : visualiser la chaîne de valeur

- mettre en évidence le processus commun
- offrir une vision globale
- obtenir le consensus (regarder autour de son activité)

#### Principe 2 : limite de WIP

- mettre en place un flux tiré
- éviter les micro-optimisations
- éviter le multi-tasking
- dégager du temps libre (quand on est en attente des autres)

--> pas mal, le problème vient tout de même du bypass par les boards annexes (Engineering). On ne devrait taper dedans que pendant le temps libre.

#### Principe 3 : gérer le flux

- s'intéresser au débit du système, pas à celui de chaque étape
- détecter les goulots d'étranglement (les étapes, cette fois)
- utiliser la théorie des contraintes (limite WIP)

--> limiter le nombre de "bypass" avec label Critical.

#### Principe 4 : rendre le process explicite

- chaque étape est claire, avec les règles d'entrée et de sortie

--> ajouter une carte "descriptive" des entrées / sorties de chaque board + principe.

#### Principe 5 : mettre en place des boucles de feedback

- multiplier les opportunités d'amélioration
- faire intervenir les différents intervenants + clients

#### Principe 6 : amélioration continue collaborative

- faire sauter les goulots d'étranglement = comment faire pour améliorer les choses quand c'est nécessaire
- obtenir l'engagment de tous par le consensus

### Dans quel contexte on l'applique ?

- lorsque l'on veut reporter la décision au plus tard (limite de Story Queue)
- lorsque le flux de travail n'est pas équilibré et que ça induit des problèmes (blocages, tâches non prévues, etc.)
- lorsque la chaîne de travail est surchargée

--> il faudrait vraiment limiter les bypass par label + boards annexes

### Par où commencer ?

1. visualiser le flux de travail existant
2. commencer là où on en est
3. avec des règles claires et explicites
4. faire des améliorations validées (évolution plutôt que révolution)

Plus qu'une méthodologie : le Kanban est un process d'amélioration de process.

--> imposer les tâches "mandatory" DANS la board principale. Les autres board, c'est du "temps libre".

--> une autre solution, c'est *d'affecter* un rôle à chacun sur les boards de production (Current Development, Bugs, Support) pour voir quels sont les *effectifs* de production. Ainsi, pas de multi-tasking à gérer (c'est le but). Les boards annexes (Engineering, Arts, etc.) sont là pour le temps libre.

--> supprimer le concept de "Yes we'll do that" des boards *temps libre*.

## 2. Du management visuel à l'obeya

Les piliers de Scrum : apprentissage, décision, inspection, adaptation.

Faire attention lors de l'affichage de l'information de bien présenter l'objectif !

Go voir <http://hakanforss.wordpress.com> pour quelques exemples.

Critères :
- univoque (clair pour tout le monde)
- visible (il faudrait l'afficher dans le bureau, genre une télé si y'a Trello)
- interactif pour permettre à chacun de s'engager, se mettre en mouvement

--> laisser chacun MAJ le Trello correctement

--> rendre visible les metrics de performance & co.

--> enlever les trucs useless, ne laisser que les trucs **utiles**

Download le petit guide du management lean sur <http://leanagilecamp.fr>.

## 3. Résolution des obstacles avec A3

--> évolution de la board Support

OK pour tableau différent \o/

--> illustrer le classement des bugs selon une matrice de risques avec 2 labels **urgent** et **impact fort**. L'idée c'est de prioriser les bugs à traiter.

--> quand il y a un obstacle qui ne dépend pas de l'équipe (genre… Les Grappes), assigner une personne responsable et mettre en place des règles d'escalade.

--> faire un CFD pour la board Support et la board Bugs… en fait, pour toutes les boards mandatory.

Problème récurrent : un problème qui revient régulièrement. Pour cela, il faut prendre le temps de décortiquer le problème pour revenir à la racine de celui-ci (préférable au hotfix… mais hotfix peut dépanner rapidement).

Méthodologies classique de recherche de cause racine : 5 Whys, fishbone diagram, Pareto diagram, etc.

--> cela dit sans déconner, au prochain bug un peu chiant, essayer de faire pratiquer les méthodologies de recherche de cause racine à l'équipe.

## 4. PDCA

--> à implémenter aussi : prendre le temps (une matinée) de temps en temps pour se poser et réfléchir à comment s'améliorer.

## 5. Metrics

1. **Lead Time** = Time To Market pour qu'une task traverse le flow jusqu'à la production
1. **Cycle Time** = Temps de passage dans un processus
1. **Débit** = nombre de features livrées sur une période donnée
1. **WIP** = nombre de en-cours (illustrés dans le CFD)
1. **Efficience** = détermine la proportion de temps passé à créer de la valeur ajoutée

### Liens entre les metrics

**WIP = Débit * Lead Time**

Il suffit de réduire le nombre de WIP pour augmenter son débit donc =)

Avec un encours stable et le débit il est facile de prédire quand une activité sera terminée. Au delà de 50 WIP, ça devient plus compliqué…

**Efficience = Cycle Time / Temps d'attente**

Pour l'efficience, on met un indicateur tampon pour savoir combien de temps une feature est restée "en attente".

On peut appliquer tout ça à TOUTES les boards actives.

On remarque au final que les estimations faîtes ne servent pas à grand chose parce-que factuellement ce ne sera pas vrai. Donc ne pas perdre de temps avec ça.

On peut créer un tableau de bord clair et efficace :
- cycle time
- nb cartes
- débit moyen / jour
- pas de variabilité
- variabilité 20%
- variabilité >20%

On le fait en matrice, par "step".

On peut faire le VSM (Value Stream Mapping) des steps pour cartographier ce qui se passe sur un domaine donné, comme les gaspillages(cycle time par step + temps d'attente global).

## Questions à résoudre pour Metidia

### Process avec étapes potentiellement facultatives

Comment le représenter ? Actuellement on crée une board par process… mais du coup on a 2 / 3 boards en parallèle à gérer.

#### Réponse

Pas un soucis. La carte passe par les steps qui lui incombent. Elle attend dans la step précédente en attendant que la suivante la libère.

Par exemple, une feature qui impliquerait GD/Market et Dev, mais pas de Graphisme :
- d'abord dans Story Queue
- dans **GD / Marketing** quand ils peuvent s'en occuper
- puis dans **Development** quand ils pourront s'en occuper. En attendant, elle prend une place dans **GD / Marketing**. Ça illustre la réalité du flow avec la capacité des devs à enchaîner (si y'a des cartes en mode bypass dans les autres boards, c'est normal que ça bloque la production, faut pas se le cacher).

### Process avec étapes pouvant être parallélisées

Comment faire ? Est-ce une bonne idée ?

#### Par exemple

Il est tout à fait possible de lancer le dév sur l'implémentation des algorithmes et de la logique des specs sans s'attaquer à l'intégration graphique.

Pendant ce temps, les graphistes peuvent travailler sur les ressources, en parallèle.

Une fois que les mockups sont sorties, les devs peuvent attaquer le graphisme.

Une fois que les resources graphiques sont produites, les graphistes peuvent eux-même intégrer et voir le résultat. Moyennement quelques ajustements, on est rendu.

Le soucis, c'est que ce sont 2 process qui peuvent être parallélisés, avec des checkpoints de synchronisation. Bref, c'est pas purement linéaire.

La question c'est donc : peut-on le représenter en Kanban ? Si oui, comment ?

#### Réponse

En fait, en production continue ça ne change rien en terme de débit. On produira exactement à la même vitesse, contrairement à ce qu'on peut penser, parce-qu'il ne faut pas oublier qu'on produit en flux tiré !

En revanche, ça va compléxifier le flow et ça risque de générer des temps d'attente supplémentaire par erreurs de synchronisation et re-travail nécessaire quand les trucs "arrivent finalement". Ce n'est pas le cas si "tout y est" quand on commence à dev en fait.

Bref : **mauvaise idée**.

### WIP plus d'actualité dans le flow

Une carte qui a été mise dans le flow mais qui, finalement, devient gênante, peut-elle être killed ?

On peut imaginer une carte qui avait été planifiée et commencé à être traitée… mais finalement la demande est telle qu'on doit urgemment traiter d'autres cartes (et on ne veut pas abuser du label de bypass, sinon ça n'a plus de sens).

#### Réponse

On peut complètement la kill ! Les besoins market passent avant tout, sinon ça n'a pas de sens.

Par contre, ça coûte. En mettant en place des indicateurs on pourra noter l'impact de ce qui s'est passé pour sensibiliser la prochaine fois. Essayer de chiffrer le coût (temps perdu sur un travail non fourni).

Bref : **oui, mais faut éviter d'avoir à le faire parce-que ça coûte**.

## TODO à Metidia

1. Définir les boards de process VS les boards de temps libre, les indiquer clairement dans le nom des boards
2. Repasser toutes les cartes de process dans les boards de process
3. Kill les cartes qui doivent l'être en le notant dans le pilotage
4. Définir les indicateurs dont on a besoin
5. Corriger les indicateurs actuels et mettre en place suivi des indicateurs manquants
6. Labels **urgent** et **fort impact** dans board Bugs (pour priorisation)
7. Mettre en place CFD et suivi indicateurs pour toutes les boards process
