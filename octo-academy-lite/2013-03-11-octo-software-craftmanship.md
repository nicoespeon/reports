# OCTO - SOFTWARE CRAFTMANSHIP (FR)

## Mise au point terminologique

Ce qui va suivre peut s'appliquer partout. Notamment dans le cadre des méthodes agiles, alors ces pratiques sont indispensables.

Niveau 0 de collaboration :

- vision claire de l'objectif commun
- liste des tâches partagée
- gestionnaire de code source (gestion de conflit, centralisation, contrôle de version)

### Pourquoi l'artisanat logiciel ?

La **carrière de développeur** peut être tout aussi **prestigieuse** que celle de manager ou de consultant.

Le défi à relever est de pouvoir livrer du logiciel en continue, sans avoir de régression sur ce qui a été livré et sur les maintenances futures.

## Un développeur responsable

Une posture, des pratiques :

- qualité non-négociable
- amélioration continue
- pragmatisme

L'artisan codeur va poser les fondations pour une agilité sécurisée.

Il doit disposer d'un éventail de compétences :

- archi et build
- qualité de code
- attitude

### Architecture, conception pragmatique

**KISS** - n'implémenter que ce qui est absolument nécessaire.
**YAGNI** (*You Ain't Gonna Need It*) - éviter le surdesign, on ne sort que les outils dont on a besoin.

Croissance organique du logiciel : on remodèle en permanence, y compris l'architecture. C'est dangereux ? Oui... et non. En théorie on fonctionne par itérations très courtes.

Pour fonctionner par itérations, il faut s'équiper d'un harnais de sécurité :

- tests pour valider le comportement de mon module
- tests mettant en évidence les régressions
- minimisant le coût de correction du défaut

On conseille d'exécuter fréquement les tests pour pouvoir les débusquer (et corriger) rapidement.

Tout est testable... après c'est une question d'investissement :

- temps d'écriture, d'éxecution et de maintenance
- coût de l'anomalie / régression

Les **tests unitaires** sont la base, on en a beaucoup. Par dessus, il faudrait rajouter des **tests fonctionnels** plus haut niveau, qui testent les fonctionnalités de l'application.

Enfin, il faut mettre en place des **tests critiques**. Ils sont beaucoup moins nombreux mais ce sont ceux qui font tourner la boite : on teste le tunnel de commande sur un site e-commerce ! Ce sont des tests fonctionnels... mais ce qu'il ne faut pas oublier.

Les tests unitaires doivent être **clairs et explicites**. En théorie aussi... faut les écrire avant (TDD, BDD).

Avec la TDD :

- j'ai la garantie d'écrire mes tests
- je met en évidence l'absence d'un comportement
- je suis le premier client de mon API (je peux donc la modeler pour qu'elle soit simple)
- je vais pouvoir valider la complétude de mon implémentation
- je peux garantir la non-régression du code précédent \o/

## Une équipe responsable

### Enjeu de la lisibilité

On passe 10 fois plus de temps à le lire qu'à l'écrire. Le code doit être facile à parcourir, qu'il soit explicite et bien structuré, facile à modifier... en toute sécurité (évidemment).

### Propriété collective du code

Le code appartient à tous les membres du projet. De nombreuses pratiques favorisent ce partage :

- revues de code
- pair programming
- dojos (exemple de *coffee machine*, s'entraîner sur des techniques nouvelles sur d'autres terrains de jeu que le code du projet)

Cela facilite la montée en compétences, la diffusion des pratiques, prévenant ainsi le **syndrome de l'homme-clef**.

Amélioration continue : ces pratiques partagées constituent les standards de l'équipe. Ces standards évolueront par divers biais :

- formation personnelle
- revues de code
- rétrospectives

## Pratiques avancées

Intégration continue, Continuous Delivery, ... Flickr livre 10 fois par jour. Avec le **feature flipping** je peux décorreller la livraison du code et celle de fonctionnalités !

C'est un investissement sur le long terme. C'est un perfectionnement individuel qui doit profiter à tous.

C'est une forme de "design patterns" sur l'écriture du code.
