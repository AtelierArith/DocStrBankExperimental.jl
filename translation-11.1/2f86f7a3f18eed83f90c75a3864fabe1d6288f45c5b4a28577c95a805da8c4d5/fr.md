```
ntuple(f, ::Val{N})
```

Crée un tuple de longueur `N`, en calculant chaque élément comme `f(i)`, où `i` est l'index de l'élément. En prenant un argument `Val(N)`, il est possible que cette version de ntuple génère un code plus efficace que la version prenant la longueur comme un entier. Mais `ntuple(f, N)` est préférable à `ntuple(f, Val(N))` dans les cas où `N` ne peut pas être déterminé à la compilation.

# Exemples

```jldoctest
julia> ntuple(i -> 2*i, Val(4))
(2, 4, 6, 8)
```
