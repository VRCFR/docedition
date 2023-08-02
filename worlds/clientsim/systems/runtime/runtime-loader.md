


# RuntimeLoader
Le RuntimeLoader est une classe statique responsable du démarrage de ClientSim lors de l'entrée en mode lecture. Il utilise le crochet InitializeOnLoad d'Unity pour vérifier l'instance des paramètres afin de déterminer si ClientSim doit démarrer, et crée une instance de ClientSimMain. Cette classe gère également la suppression des objets utilisés uniquement dans l'éditeur dans la scène. Afin de permettre la testabilité de ClientSim, plusieurs méthodes sont disponibles pour définir les paramètres de test et les remplacements des dispatchers d'événements.