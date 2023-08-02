

# Tests Automatisés

ClientSim dispose de nombreux tests différents pour vérifier le comportement du programme. La majorité des tests sont des tests d'intégration, mais il est également possible d'effectuer des tests unitaires. Consultez TestRunner Unity pour visualiser tous les tests. Lors de l'importation de ClientSim en tant que package, les tests peuvent être activés en ajoutant la ligne suivante au manifeste du projet après la section `"dependencies" :{}` :
```json
"testables": [
  "com.unity.inputsystem",
  "com.vrchat.clientsim"
]
```

Une fois ajoutés, Unity importera les tests et vous les verrez apparaître dans la fenêtre Test Runner.

![Test Runner](/images/test-runner.png)

## Tests Unitaires

ClientSim dispose de quelques tests unitaires qui peuvent vérifier des éléments en dehors du mode Play de Unity. D'autres éléments peuvent être refactorisés pour être dissociés des MonoBehaviours afin d'être plus facilement testables unitairement.

## Tests d'Intégration

ClientSim dispose désormais d'un framework de tests d'intégration complet qui teste la majorité des fonctionnalités incluses. Ce framework permet d'envoyer des événements d'entrée et d'écouter les événements de ClientSim pour vérifier si l'action appropriée s'est produite. Ce framework peut également être utilisé pour les mondes afin de vérifier des comportements spécifiques, permettant aux utilisateurs de créer leurs propres tests.

### Configuration des Tests

En raison de la manière dont ClientSim démarre en utilisant InitializeOnLoad, les tests nécessitent de modifier les paramètres de l'éditeur Unity pour valider correctement le comportement. Dans l'environnement de test, InitializeOnLoad se produit avant le démarrage du mode Play. Le paramètre par défaut de Unity a la rechargement du domaine activé lors de l'entrée en mode Play. Cela signifie que lors du passage en mode Play, toutes les données variables sont effacées. Pour contourner ce problème, tous les tests de ClientSim doivent être exécutés avec le rechargement du domaine désactivé. Cela est géré automatiquement pour tous les tests qui dérivent de l'une des deux classes de base de test : ClientSimTestBase et ClientSimWorldTestBase. 

### Aides aux Tests

Les deux objets clés de test d'intégration sont accompagnés de méthodes d'aide qui permettent de vérifier des comportements spécifiques.

* **ClientSimTestHelpers** - Cette classe contient des méthodes d'aide pour effectuer des actions utiles ainsi que des écouteurs pour différents événements de ClientSim afin de vérifier l'exécution des actions.

* **ClientSimTestInput** - Cette classe permet à l'utilisateur de définir la valeur de n'importe quel événement d'entrée basé sur le bureau.

### ClientSimTestBase

Les objets de test qui dérivent de cette classe servent à tester des prefabs individuels plutôt que des mondes entiers. Au début du test, le comportement par défaut de ClientSim est désactivé. Il est possible de charger un monde ou de créer un prefab, mais ClientSim doit être démarré manuellement. Selon l'ordre, le comportement sera différent par rapport au démarrage normal de ClientSim via le mode Play. 

1. Si un monde ou un prefab est chargé avant le démarrage de ClientSim, alors tout composant VRC SDK ne se connectera pas à ClientSim et démarrera comme si ClientSim était désactivé. Les points de spawn des joueurs fonctionneront comme prévu dans ce cas, car le VRC_SceneDescriptor est nécessaire pour démarrer ClientSim et faire apparaître un joueur.
2. Si un monde ou un prefab est chargé après le démarrage de ClientSim, alors tous les composants VRC SDK s'initialiseront avec les comportements de ClientSim comme dans le mode Play normal. Dans ce cas, cependant, le joueur aura déjà été créé et ne sera pas placé au point de spawn du monde chargé. 

La majorité des tests de ClientSim sont écrits dans ce format. Une scène contenant les composants minimaux nécessaires pour démarrer ClientSim est chargée, ClientSim est démarré, et à partir de là, les tests effectuent ce qui est nécessaire, comme l'appel de l'API SDK appropriée ou la création de prefabs tout en simulant des événements d'entrée. 

Voici la liste des tests d'intégration :

#### Tests d'Initialisation
* Teste le comportement du démarrage de ClientSim en fonction des différents paramètres et des objets de scène initiaux.

#### Tests des Aides
* Teste le comportement des différentes classes d'aide du SDK ClientSim. AudioSpatializer, AVProVideoPlayer, ObjectPool, ObjectSync, composant Udon sans programme, UIShape.

#### Tests d'Interaction
* Teste le système d'interaction pour la manipulation des objets interactifs. Notez que, comme Udon ne peut pas être correctement inclus dans les packages en raison de la nécessité de références externes et de compilations fréquentes, ce test utilise un script d'objet interactif fictif.

#### Tests de Ramassage
* Teste le système d'interaction, la main du joueur et l'entrée dans différentes situations de ramassage.

#### Tests de l'API du Joueur
* Teste le comportement de toutes les méthodes exposées relatives à VRCPlayerApi.

#### Tests du Contrôleur du Joueur
* Teste les paramètres de locomotion du joueur.

#### Tests de Station
* Tests utilisant des stations et comportement attendu avec elles.

#### Tests d'Interface Utilisateur (UI)
* Teste les interactions avec l'interface utilisateur Unity en utilisant le composant VRC_UIShape.

### ClientSimWorldTestBase

Les objets de test qui dérivent de cette classe servent à tester des mondes complets et à vérifier le démarrage de ClientSim pour le monde donné. Le test doit charger un monde donné dans la phase de configuration du test, puis ClientSim démarrera normalement comme s'il n'était pas dans l'environnement de test en entrant en mode Play. Étant donné que ClientSim démarre normalement, un seul test peut être exécuté à la fois car le mode Play n'est démarré qu'une seule fois pour tous les tests. Si plusieurs tests sont exécutés ensemble, ils échoueront tous immédiatement avec un avertissement indiquant qu'un seul test peut être exécuté à la fois.

Trois tests de monde sont fournies par défaut :
#### Aucun descripteur de monde
* Teste si ClientSim échoue à démarrer si une scène est chargée sans descripteur de monde.

#### Deux joueurs
* Démarre ClientSim normalement dans un monde basique, fait apparaître un joueur distant et vérifie toutes les données sur les deux joueurs.

#### WorldTestExample
* Il s'agit d'un exemple de test montrant comment un utilisateur peut écrire des tests pour son monde. Le test est inclus en tant qu'exemple pour le package ClientSim et doit être importé. Ce test montre comment vérifier un monde "Puzzle" simple.