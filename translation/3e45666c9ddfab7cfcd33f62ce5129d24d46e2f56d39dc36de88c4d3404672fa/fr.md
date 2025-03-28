```
treewalk(f, tree::GitTree, post::Bool=false)
```

Parcourt les entrées dans `tree` et ses sous-arbres en ordre post ou pré. L'ordre pré signifie commencer à la racine, puis parcourir le sous-arbre le plus à gauche (et récursivement à travers les sous-arbres les plus à gauche de ce sous-arbre) et se déplacer vers la droite à travers les sous-arbres. L'ordre post signifie commencer par le bas du sous-arbre le plus à gauche, remonter à travers celui-ci, puis parcourir le sous-arbre de droite suivant (encore une fois en commençant par le bas) et enfin visiter la racine de l'arbre en dernier.

Le paramètre de fonction `f` doit avoir la signature suivante :

```
(String, GitTreeEntry) -> Cint
```

Une valeur négative retournée par `f` arrête le parcours de l'arbre. Une valeur positive signifie que l'entrée sera ignorée si `post` est `false`.
