

# TooltipManager

Le TooltipManager affichera un texte dans le monde au-dessus d'un objet interactif donné. Les tooltips dans ClientSim ne présentent que du texte, contrairement à VRChat qui affiche également une icône du bouton correspondant nécessaire pour utiliser l'interaction. Dans SDK3, il semble que l'option pour définir l'emplacement d'un tooltip pour un objet interactif soit ignorée. Les tooltips s'affichent toujours au centre supérieur du premier collider de l'objet interactif. Il n'y a pas de limite établie au nombre de tooltips pouvant être affichées, mais seulement 2 tooltips sont attendues via ClientSim, un par main du joueur. L'affichage des tooltips peut être désactivé dans les [ClientSimSettings](settings.md).