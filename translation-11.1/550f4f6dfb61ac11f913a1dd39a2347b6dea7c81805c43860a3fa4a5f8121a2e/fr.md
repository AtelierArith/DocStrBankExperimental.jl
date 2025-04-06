```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

Vue `N`-dimensionnelle dans un tableau parent (de type `P`) avec un type d'élément `T`, restreint par un tuple d'indices (de type `I`). `L` est vrai pour les types qui supportent l'indexation linéaire rapide, et `faux` sinon.

Construisez des `SubArray`s en utilisant la fonction [`view`](@ref).
