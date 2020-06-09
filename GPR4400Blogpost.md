# Blogpost Technique
## Génération procédurale d’une maison en 2D sur Unity avec un BSP (Binary Space Partitioning)

### Introduction :

Lors d’un projet scolaire à la SAE pour le module GPR4400.2, nous devions, par équipe de 2 personnes, implémenter une IA et une génération procédurale. Je me suis occupé de cette dernière en utilisant un algorithme BSP pour faire une maison qui est différente à chaque nouvelle partie. J’ai suivi ce tutoriel tout en l’adaptant à notre jeu : [http://www.rombdn.com/blog/2018/01/12/random-dungeon-bsp-unity/](http://www.rombdn.com/blog/2018/01/12/random-dungeon-bsp-unity/)

### Créer les salles :
Dans le tutoriel, le bsp était généré sans tilemap et s’affichait ensuite sur Unity. Pour notre jeu, il fallait que j’utilise deux tilemaps : une pour le sol (avec les couloirs) et une autre pour les murs.
J’ai instancié ces variables :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt4.PNG)
 
Puis je les ai utilisées dans une fonction pour dessiner les salles :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt3.PNG)
 
Au lieu d’utiliser ce qui est en commentaire, j’ai utilisé le tilemap.SetTile avec g_Tile, où j'ai pu ensuite mettre la tile blanche sur l'inspecteur d'Unity, me donnant ce résultat:

![](https://eleonoradps.github.io/BlogPostTechnique/itsMinePres4.PNG)
 
Mais ça ne ressemble pas vraiment à une maison, à ce moment là ce n’était que des carrés/rectangles séparés les uns des autres. Le problème venait de cette ligne de code :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt2.PNG)
 
 Afin de régler ce problème, j’ai fait la largeur et la hauteur moins 2, au lieu de l’addition roomX et roomY aux rectangle.x et rectangle.y :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt1.PNG)
 
Pour ensuite donner ça :

![](https://eleonoradps.github.io/BlogPostTechnique/blogposttechnique.PNG)
 
### Lier les salles à l’aide de couloirs :

Je devais maintenant connecter les salles entre elles, et après avoir fait le code, les couloirs ne s’affichaient pas. J’essayais de créer des couloirs entre des Leafs qui n’ont pas d’enfants, ce qui faisait que ma fonction ne s’exécutait pas. Le problème a été réglé en ajoutant une condition qui lient les salles si ce ne sont pas des Leafs.

![](https://eleonoradps.github.io/BlogPostTechnique/bpt5.PNG)

![](https://eleonoradps.github.io/BlogPostTechnique/blogposttechnique2.PNG)

### Afficher les murs avec une deuxième Tilemap :

Mon autre problème était l’affichage des murs. En premier lieu, j’avais fait une fonction avec des for :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt8.PNG)
 
Après avoir mis des Debug.Log, le problème était qu’on ne connaissait pas les positions des subRoom.Room.x et subRoom.Room.y. Je les ai ensuite remplacés par boardRows et boardColumns, qui symbolise la taille du rectangle de mon BSP :

![](https://eleonoradps.github.io/BlogPostTechnique/screen.PNG)
 
Mais ça ne marchait toujours pas. Après 2-3 jours et en discutant avec un autre programmeur, mon problème venait du fait que dans ma boucle for, je ne donnais pas la position exacte du int i et int j pour la première déclaration.

![](https://eleonoradps.github.io/BlogPostTechnique/bpt6.PNG)
 
Après ces modifications, le BSP s’affichait ensuite comme ceci :

![](https://eleonoradps.github.io/BlogPostTechnique/bpt9.PNG)
 
Nous avons donc maintenant une maison qui se génère procéduralement, avec deux tilemaps.

![](https://eleonoradps.github.io/BlogPostTechnique/bpt10.PNG)

### Lien git du projet :
[https://github.com/eleonoradps/ItsMine]( https://github.com/eleonoradps/ItsMine)

