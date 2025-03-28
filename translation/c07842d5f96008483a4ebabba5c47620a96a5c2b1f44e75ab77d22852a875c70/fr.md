```
deepcopy(x)
```

Crée une copie profonde de `x` : tout est copié récursivement, ce qui donne un objet entièrement indépendant. Par exemple, la copie profonde d'un tableau crée des copies profondes de tous les objets qu'il contient et produit un nouveau tableau avec la structure de relation cohérente (par exemple, si les deux premiers éléments sont le même objet dans le tableau original, les deux premiers éléments du nouveau tableau seront également le même objet `deepcopy`é). Appeler `deepcopy` sur un objet devrait généralement avoir le même effet que de le sérialiser puis de le désérialiser.

Bien qu'il ne soit normalement pas nécessaire, les types définis par l'utilisateur peuvent remplacer le comportement par défaut de `deepcopy` en définissant une version spécialisée de la fonction `deepcopy_internal(x::T, dict::IdDict)` (qui ne devrait pas être utilisée autrement), où `T` est le type à spécialiser, et `dict` garde une trace des objets copiés jusqu'à présent dans la récursion. Dans la définition, `deepcopy_internal` doit être utilisé à la place de `deepcopy`, et la variable `dict` doit être mise à jour comme il se doit avant de retourner.
