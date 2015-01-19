# Backbone.js Paris - 27/03/14 (FR)

## Bases et initialisation d'un projet

Présenté par Jonathan Jalouzot - [@jonathanj33](https://twitter.com/jonathanj33) (back-end).

Dans l'ensemble rien de neuf. Mauvais départ (Backbone = framework MVC... mouais, défaut de vision d'un dev back-end PHP).

Cela dit TDD intéressante.

**Karma** a l'air de s'initialiser plus simplement (et proprement) qu'Istambul avec require.js et Grunt.


## Multipage webapp

Présenté par [@vrabanelly](https://twitter.com/vrabanelly) (lead dev front [@drivy](https://twitter.com/drivy)).

172 fichiers Coffee / JS dont seulement 14 avec plus de 100 lignes. Décomposition en multiples fichiers intéressantes -> décompilation des modules plus ou moins nécessaire avec renommage.

Comment structurer une grosse appli ? C'est le sujet.

### Namespacing

```javascript
window.Drivy = {
  Views: {
    Booking: {
      Steps: {}
    },
    Cars: {},
    (...)
  }
}
```

*Remarque : beaucoup de dépendance directe entre leurs modules. Ils devraient utiliser de la DI pour donner une couche d'abstraction et de robustesse.*

Leur organisation réplique leur organisation back-end finalement (72% de Ruby sur le projet). Le point de vue est un peu biaisé, on ne part pas de l'appli mais du back-end déjà prêt et on adapte le front pour que ce soit confort pour les devs back-end.

### View auto loading

Là encore, on map les actions du server avec le front (on adapte le front au back quoi).

Intéressant : utiliser les `data-*` pour générer des comportements automatiques du front (un peu comme AngularJS).

*Remarque : les mecs utilisent à moitié JS, à moitié Coffee. Ils sont partis sur Coffee parce-qu'ils peuvent reproduire des syntaxes back-end (classes & co.) qui sont compilées en équivalent JS... Bref des devs back-end Ruby.*

## Marionette

Présentation des fonctionnalités de Marionette. Cf. la doc de Marionette en fait =)

On peut utiliser les initializer de Marionette pour gérer le waterfall des modules.

Fonction `getTemplate()` si jamais on a besoin de définir un switch de template dans une vue (sait-on jamais).

Note : a priori on peut mettre plusieurs handlers dans les tableaux d'association d'events.

```javascript
modelEvents: {
  "change": "doThis doThat"
}
```

## Randori

Pratique de code par pair avec un chrono de 5min, sur une problématique.

Le TP ce coup-ci c'est de recoder [2048](gabrielecirulli.github.io/2048/).
