```
ceil([T,] x)
ceil(x; digits::Integer= [, base = 10])
ceil(x; sigdigits::Integer= [, base = 10])
```

`ceil(x)` renvoie la valeur entière la plus proche du même type que `x` qui est supérieure ou égale à `x`.

`ceil(T, x)` convertit le résultat en type `T`, en lançant une `InexactError` si la valeur arrondie n'est pas représentable en tant que `T`.

Les mots-clés `digits`, `sigdigits` et `base` fonctionnent comme pour [`round`](@ref).

Pour prendre en charge `ceil` pour un nouveau type, définissez `Base.round(x::NewType, ::RoundingMode{:Up})`.
