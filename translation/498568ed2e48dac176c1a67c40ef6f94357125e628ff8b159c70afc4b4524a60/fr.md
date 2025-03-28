```
setindex!(A, X, inds...)
A[inds...] = X
```

Stockez des valeurs du tableau `X` dans un sous-ensemble de `A` tel que spécifié par `inds`. La syntaxe `A[inds...] = X` est équivalente à `(setindex!(A, X, inds...); X)`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
