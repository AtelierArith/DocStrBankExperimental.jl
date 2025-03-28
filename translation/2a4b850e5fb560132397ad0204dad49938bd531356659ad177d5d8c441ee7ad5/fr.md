```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

Une plage `r` où `r[i]` produit des valeurs de type `T` (dans la première forme, `T` est déduit automatiquement), paramétrée par une valeur de `ref`érence, un `step`, et la `len`gth. Par défaut, `ref` est la valeur de départ `r[1]`, mais vous pouvez alternativement la fournir comme la valeur de `r[offset]` pour un autre index `1 <= offset <= len`. La syntaxe `a:b` ou `a:b:c`, où l'un des `a`, `b` ou `c` est un nombre à virgule flottante, crée un `StepRangeLen`.

!!! compat "Julia 1.7"
    Le 4ème paramètre de type `L` nécessite au moins Julia 1.7.

