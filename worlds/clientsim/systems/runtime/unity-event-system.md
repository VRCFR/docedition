

# Système d'événements Unity

ClientSim utilise deux classes pour traduire les actions dans le système d'événements d'Unity. Ces classes dissocient l'ancien système de saisie d'Unity en valeurs basées sur les liaisons actuelles de ClientSim et correspondent à la filtration des objets d'interface utilisateur interactifs de VRChat.

## BaseInput

Le système ClientSimBaseInput étend la classe BaseInput d'Unity. La classe BaseInput d'Unity est responsable de la transmission de la position de la souris et des entrées de bouton dans le système d'événements. Le système ClientSim BaseInput remplace ces méthodes afin de transmettre les valeurs basées sur les liaisons d'entrées ClientSim actuelles et les résultats du dernier [PlayerRaycaster](player.md#raycaster). L'entrée de la souris est remplacée par l'entrée d'utilisation [Use Input](input.md) actuelle. Étant donné que l'entrée Utilisation est une action à deux mains, seule la valeur de la dernière main activée est transmise comme entrée de souris. La position de la souris envoyée au système d'événements ignore la position réelle de la souris et calcule plutôt la position de l'écran du dernier rayon d'interaction. L'utilisation de la position du rayon abstrait la position réelle de la souris, permettant ainsi à Desktop et à VR d'utiliser l'interface utilisateur Unity par le biais du même système.
Le système BaseInput est également responsable de fournir la position actuelle de la souris au reste de ClientSim. Il contrôle si le pointeur de la souris est caché et verrouillé au centre de l'écran ou visible et libre de se déplacer. Cette position de la souris est utilisée pour afficher le [Réticule du Bureau](player.md#reticle) ainsi que pour utiliser la souris pour créer la direction du rayon pour [DesktopRayProvider](player.md#rayprovider).

## InputModule

Le ClientSimInputModule étend la classe StandaloneInputModule d'Unity. Ce système traite les événements de la souris d'Unity et filtre les objets d'interface utilisateur qui ne sont pas actuellement interactifs. Les objets d'interface utilisateur sont interactifs lorsque toutes les conditions suivantes sont remplies :

1. Le [PlayerRaycaster](player.md#playerraycaster) a touché un objet avec un composant VRC_UIShape. Ces données sont fournies par ClientSimBaseInput.
2. L'objet d'interface utilisateur a un composant UIShape dans son parent.
3. La couche de l'objet parent UIShape est sur une couche interactive actuellement. Les couches interactives sont déterminées par le [InteractiveLayerProvider](interactive-layer-provider.md).
4. Le point de contact du rayon de l'objet d'interface utilisateur est contenu à l'intérieur du collider de l'UIShape. Si l'une de ces conditions échoue, l'interface utilisateur ne peut pas être utilisée.