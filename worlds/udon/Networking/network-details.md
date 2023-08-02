

# Conseils

Essayez de ne pas tout synchroniser ; réfléchissez à ce que vous pouvez déduire à partir d'un minimum d'informations partagées. Par exemple : si un objet se déplace sur un trajet fixe ou prévisible, sa position n'a peut-être pas besoin d'être synchronisée et il suffira de connaître sa position initiale et sa vitesse.

Si la logique du jeu est compliquée, essayez de la placer sur un seul objet ; partager des états de logique importants entre plusieurs objets peut entraîner une désynchronisation en raison de différences de propriété.

La synchronisation continue est destinée aux données qui changent fréquemment et pour lesquelles les valeurs intermédiaires n'ont pas d'importance ; comme la position d'une transformation se déplaçant de manière erratique. VRChat effectuera une approximation des valeurs intermédiaires pour récupérer les données perdues et tentera d'optimiser les données réseau pour une synchronisation continue.

La synchronisation manuelle est destinée aux données qui changent rarement et pour lesquelles les valeurs intermédiaires sont importantes ; comme les positions des pièces sur un échiquier.
**Les utilisateurs ne doivent pas s'attendre à des mises à jour rapides avec une sérialisation manuelle.**

Si vous avez plusieurs UdonBehaviours sur un objet, la méthode de synchronisation sera celle des réglages les plus restrictifs - un UdonBehaviour manuel et un UdonBehaviour continu sur le même objet seront tous deux considérés comme manuels.

# Données et spécifications
Note : toutes les spécifications sont susceptibles de changer, elles seront mises à jour ici si c'est le cas.

Vous pouvez voir des informations spécifiques sur les données utilisées par objet dans la vue de débogage 6.

La synchronisation continue est limitée à environ **200 octets** par sérialisation.

La synchronisation manuelle est limitée à environ **49 kilo-octets** par sérialisation.

Chaque objet synchronisé manuellement est limité en fonction de la taille des données. Plus il envoie de données, plus son taux d'envoi est limité. Vous pouvez appeler RequestSerialization autant de fois que vous le souhaitez, mais cela attendra suffisamment de temps avant d'appeler OnPreSerialization, d'envoyer les données et d'appeler OnPostSerialization avec le résultat.

Une seule chaîne synchronisée peut contenir environ **126 caractères** en mode de synchronisation continue.

Vous pouvez envoyer environ **11 ko par seconde**.

La latence entre l'appel de SetOwner et l'envoi des nouvelles valeurs correspond au temps aller-retour entre l'exécuteur et le propriétaire ou, si c'est le propriétaire, entre le propriétaire et le destinataire.

Si vous dépassez les limites, l'UdonBehaviour échouera à déclencher l'événement réseau et écrira des erreurs dans les journaux. La logique de l'UdonBehaviour continuera de fonctionner, mais les données ne seront ni envoyées ni reçues.