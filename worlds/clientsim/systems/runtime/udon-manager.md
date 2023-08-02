

# UdonManager

L'UdonManager garde une trace de tous les UdonBehaviours initialisés dans la scène. Notez qu'avec le VRCSDK, un UdonBehaviour ne s'initialisera pas s'il n'a pas de programme. Cela signifie que les UdonBehaviours position-synced hérités sans programmes ne sont pas suivis, même avec le SyncedObjectManager. L'UdonManager a deux rôles principaux. Le premier est de notifier tous les Udon Helpers lorsque ClientSim a terminé son initialisation, ce qui permet aux UdonBehaviours de démarrer. Le second est d'écouter certains [événements](event-dispatcher.md) de ClientSim afin de les transmettre à tous les UdonBehaviours. Actuellement, l'UdonManager transmet uniquement les événements suivants :
* OnPlayerJoined
* OnPlayerLeft
* OnPlayerRespawn