```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

Crée un conteneur `AbstractDict` vide qui peut accepter des indices de type `index_type` et des valeurs de type `value_type`. Les deuxième et troisième arguments sont optionnels et par défaut au `keytype` et `valtype` de l'entrée, respectivement. (Si l'un des deux types est spécifié, il est supposé être le `value_type`, et le `index_type` par défaut est `keytype(a)`).

Les sous-types `AbstractDict` personnalisés peuvent choisir quel type de dictionnaire spécifique est le mieux adapté à retourner pour les types d'index et de valeur donnés, en se spécialisant sur la signature à trois arguments. La valeur par défaut est de retourner un `Dict` vide.
