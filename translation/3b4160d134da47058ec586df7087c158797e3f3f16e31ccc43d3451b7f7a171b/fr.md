```
Channel{T=Any}(size::Int=0)
```

Construit un `Channel` avec un tampon interne pouvant contenir un maximum de `size` objets de type `T`. [`put!`](@ref) appelle sur un canal plein bloque jusqu'à ce qu'un objet soit retiré avec [`take!`](@ref).

`Channel(0)` construit un canal non tamponné. `put!` bloque jusqu'à ce qu'un `take!` correspondant soit appelé. Et vice-versa.

Autres constructeurs :

  * `Channel()`: constructeur par défaut, équivalent à `Channel{Any}(0)`
  * `Channel(Inf)`: équivalent à `Channel{Any}(typemax(Int))`
  * `Channel(sz)`: équivalent à `Channel{Any}(sz)`

!!! compat "Julia 1.3"
    Le constructeur par défaut `Channel()` et le `size=0` par défaut ont été ajoutés dans Julia 1.3.

