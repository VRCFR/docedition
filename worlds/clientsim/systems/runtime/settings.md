

# Paramètres

Les paramètres du ClientSim ne sont pas un système, mais des données sur la façon de lancer le ClientSim.
### Activer le ClientSim
Le ClientSim doit-il être activé lors de l'entrée en mode lecture ? Le ClientSim est désactivé de force lors du téléchargement des mondes.

### Activer l'enregistrement de la console
Les informations de débogage doivent-elles être enregistrées dans la console ?

### Supprimer "EditorOnly"
En mode lecture, tous les objets étiquetés "EditorOnly" doivent-ils être supprimés ?

### Définir le taux de rafraîchissement cible
Le ClientSim doit-il définir le taux de rafraîchissement cible de l'application ?

### Taux de rafraîchissement cible
Le taux de rafraîchissement attendu pour Unity en mode lecture. Cela réglera à la fois Application.TargetFramerate et FixedTimeDelta.

### Délai de démarrage
Combien de temps le ClientSim doit-il attendre avant de démarrer et d'initialiser Udon ? Utilisez cela comme moyen de simuler de longs temps de chargement des mondes et de vérifier le comportement des composants Unity.

### Apparition du contrôleur du joueur
Faire apparaître un joueur contrôlable lors du démarrage du ClientSim. S'il est désactivé, un joueur local est quand même créé pour éviter les plantages des programmes Udon.

### Afficher la réticule du bureau
La réticule du bureau doit-elle être affichée ou non ?

### Afficher les infobulles
Afficher les infobulles au-dessus des objets interactifs.

### Inverser l'orientation de la souris
La coordonnée Y de la souris doit-elle être inversée ?

### Hauteur du joueur
La hauteur du joueur en unités Unity. Cela est limité entre 0.2 et 80.

### Nom du joueur local
Quel est le nom du joueur local, utilisé pour VRCPlayerApi.displayName.

### Le joueur local est-il le maître ?
Lorsqu'il est réglé sur false, un joueur distant est apparu et défini comme maître.

### Le joueur local est-il propriétaire de l'instance ?