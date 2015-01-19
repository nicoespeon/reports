# Node.js Paris - 12/03/14 (FR)

## Les Streams en node.js

Un stream est un flux de données directionnel et ordonné.

Avec **node v0.10**, les streams sont passés d'un système **PUSH** stream à un système de **PULL** stream.

Paraît que socket.io est plus trop maintenu. Mais en fait ça va.

## REST world

**REST** est un standard d'écriture d'une API orientée objets.

REST est persistant, stateless, uniforme, mutable, performant et portable.

### Niveaux de REST

#### Le niveau 0

On utilise directement le protocole HTTP. HTTP propose des méthodes, des codes et des headers assez pratiques par rapport à d'autres protocoles (c'est pour ça).

#### Le niveau 1

1 ressource = 1 URI.

Pas de redondance de l'information. Une URI est uniforme, c'est stateless et c'est plus facile à retenir.

**Cool URIs don't change** : uniquement des noms, pas de verbes ni de numéro de version. `/clients` pour une liste de clients, `/clients/` redirige, consistance des URLs, ce doit être un *no-brainer*.

On peut même rajouter des termes lisibles statiques et uniques pour la SEO (genre `/machines/1139-honda`).

Toute l'intelligence est stockée dans les paramètres ici (format, filtres, etc.).

#### Le niveau 2

On utilise les verbes HTTP pour déterminer les 4 actions possibles avec une URL :

- GET
- POST
- PUT
- DELETE

On a aussi :

- HEAD
- OPTIONS
- PATCH
- CONNECT
- TRACE

#### Le niveau 3

On rajoute des headers et on se sert du tout comme il faut (les **ACCEPT**, les codes réponses HTTP, etc.).

Les niveaux 4 et 5 n'existent pas conventionnellement, mais derrière se cachent les notions de pouvoir faire des routes utilitaires (GET le temps moyen d'attente entre 2 bus, toussa toussa).

### Les frameworks Node.js

On en liste quelques uns :

- Flatiron
- Spumko
- KOA et KOA-ROUTE
