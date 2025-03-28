```
floor([T,] x)
floor(x; digits::Integer= [, base = 10])
floor(x; sigdigits::Integer= [, base = 10])
```

`floor(x)` renvoie la valeur entière la plus proche du même type que `x` qui est inférieure ou égale à `x`.

`floor(T, x)` convertit le résultat en type `T`, en lançant une `InexactError` si la valeur arrondie n'est pas représentable en tant que `T`.

Les mots-clés `digits`, `sigdigits` et `base` fonctionnent comme pour [`round`](@ref).

Pour prendre en charge `floor` pour un nouveau type, définissez `Base.round(x::NewType, ::RoundingMode{:Down})`.
