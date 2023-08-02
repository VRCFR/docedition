

# InteractiveLayerProvider

Le InteractiveLayerProvider écoute simplement les événements d'état d'ouverture du menu et fournit un masque de couche pour déterminer quelles couches sont actuellement interactives. Lorsque le menu est ouvert, seules les couches UI et UIMenu sont interactives. Lorsque le menu est fermé, toutes les autres couches, à l'exception de MirrorReflection, sont interactives. InteractiveLayerProvider est utilisé par les [Raycasters](player.md#raycaster) et l'[ClientSimInputModule](input.md).