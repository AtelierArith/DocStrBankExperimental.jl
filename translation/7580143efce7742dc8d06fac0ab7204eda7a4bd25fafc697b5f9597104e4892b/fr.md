```
const
```

`const` est utilisé pour déclarer des variables globales dont les valeurs ne changeront pas. Dans presque tout le code (et en particulier dans le code sensible à la performance), les variables globales doivent être déclarées constantes de cette manière.

```julia
const x = 5
```

Plusieurs variables peuvent être déclarées dans un seul `const` :

```julia
const y, z = 7, 11
```

Notez que `const` ne s'applique qu'à une seule opération `=` ; par conséquent, `const x = y = 1` déclare `x` comme constant mais pas `y`. En revanche, `const x = const y = 1` déclare à la fois `x` et `y` constants.

Notez que la "constance" ne s'étend pas aux conteneurs mutables ; seule l'association entre une variable et sa valeur est constante. Si `x` est un tableau ou un dictionnaire (par exemple), vous pouvez toujours modifier, ajouter ou supprimer des éléments.

Dans certains cas, changer la valeur d'une variable `const` donne un avertissement au lieu d'une erreur. Cependant, cela peut produire un comportement imprévisible ou corrompre l'état de votre programme, et donc cela doit être évité. Cette fonctionnalité est destinée uniquement à la commodité lors de l'utilisation interactive.
