

# Architecture

L'architecture de ClientSim se concentre sur de petits composants avec un modèle d'observateur basé sur des événements, combiné à une injection de dépendances manuelle où chaque classe est initialisée uniquement avec les dépendances dont elle a besoin. Le contrôleur de joueur inclus est basé sur des fournisseurs de dépendances génériques, ce qui permet une éventuelle extension à l'utilisation de la réalité virtuelle sans réécrire les systèmes de base.

## Modèle d'observateur

ClientSim utilise le modèle d'observateur pour envoyer des événements au sein du système, que tout le monde peut écouter sans savoir ce qui les gère. Les événements permettent de désolidariser les différents systèmes, améliorant ainsi la testabilité car un système n'a pas besoin de dépendre directement d'un autre pour envoyer des messages lorsque quelque chose se produit. Voir [EventDispatcher](runtime/event-dispatcher.md) pour plus de détails spécifiques.

## Injection de dépendances

L'architecture de ClientSim utilise une injection de dépendances gérée manuellement. Lors de la création d'un système, toutes les dépendances lui sont transmises, soit via son constructeur, soit via une méthode d'initialisation. Les dépendances sont structurées sous forme de fournisseurs, et doivent étendre une interface qui déclare les méthodes qu'elle fournit. Lorsqu'une classe a besoin d'un élément spécifique, elle dépend de l'interface du fournisseur plutôt que de la classe qui l'implémente. Cela permet d'avoir différentes implémentations du fournisseur sans que le code dépendant ait besoin de changer. Le modèle de fournisseur permet de facilement simuler les dépendances lors des tests.