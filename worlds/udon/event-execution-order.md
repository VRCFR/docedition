

Udon et Unity disposent d'événements intégrés qui sont appelés automatiquement si vous les incluez dans vos scripts. Par exemple, l'événement `Start()` s'exécute une fois pour chaque script, et l'événement `Update()` s'exécute une fois par image. Lorsque vous écrivez des scripts Udon, il est utile de savoir quel de ces événements se produit en premier.
:::note

Unity fournit une liste (incomplète) des événements intégrés, dont beaucoup sont également disponibles dans VRChat. [Voir la documentation Unity pour plus d'informations](https://docs.unity3d.com/Manual/ExecutionOrder.html)
:::
Le diagramme suivant montre l'ordre d'exécution des événements les plus importants disponibles dans Udon et Unity.

![Bannière d'exemple](/img/worlds/event-execution-order.svg)

:::caution

Les mises à jour d'Unity et de VRChat peuvent changer l'ordre d'exécution des événements représenté ci-dessus.
Tous les événements ne sont pas répertoriés, et certains événements peuvent être exécutés dans un ordre différent en fonction des circonstances (être le propriétaire d'un objet, rejoindre un monde tardivement, etc.)

:::