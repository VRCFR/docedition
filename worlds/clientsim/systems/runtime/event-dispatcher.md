

# Gestionnaire d'événements et événements

Le Gestionnaire d'événements est responsable de notifier les autres systèmes lorsque des événements spécifiques se produisent dans ClientSim. Un comportement peut s'abonner à un type d'événement ou envoyer un événement d'un type spécifique à tous les éléments de ClientSim sans savoir qui le gérera. Le Gestionnaire d'événements est simplement une collection de types d'événements associés à des gestionnaires d'événements. Cette méthode permet de découpler les différents systèmes de ClientSim sans avoir besoin de créer une dépendance directe. Tous les événements envoyés doivent étendre l'interface IClientSimEvent, mais peuvent contenir toutes les données nécessaires à l'événement.