```
fill(value, dims::Tuple)
fill(value, dims...)
```

Créez un tableau de taille `dims` avec chaque emplacement défini sur `value`.

Par exemple, `fill(1.0, (5,5))` renvoie un tableau 5×5 de flottants, avec `1.0` dans chaque emplacement du tableau.

Les longueurs de dimension `dims` peuvent être spécifiées soit comme un tuple, soit comme une séquence d'arguments. Un tuple de longueur `N` ou `N` arguments suivant le `value` spécifient un tableau de dimension `N`. Ainsi, un idiome courant pour créer un tableau de dimension zéro avec son seul emplacement défini sur `x` est `fill(x)`.

Chaque emplacement du tableau renvoyé est défini sur (et est donc [`===`](@ref) à) la `value` qui a été passée ; cela signifie que si la `value` est elle-même modifiée, tous les éléments du tableau `fill`é refléteront cette modification car ils sont *toujours* cette même `value`. Cela n'est pas un problème avec `fill(1.0, (5,5))` car la `value` `1.0` est immuable et ne peut pas elle-même être modifiée, mais cela peut être inattendu avec des valeurs mutables comme — le plus souvent — des tableaux. Par exemple, `fill([], 3)` place *le même* tableau vide dans les trois emplacements du vecteur renvoyé :

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

Pour créer un tableau de nombreux tableaux intérieurs indépendants, utilisez une [compréhension](@ref man-comprehensions) à la place. Cela crée un nouveau tableau distinct à chaque itération de la boucle :

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

Voir aussi : [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# Exemples

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-dimensional Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # définit les deux éléments sur le même vecteur [0.0, 0.0]
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # modifie la valeur remplie pour être [42.0, 0.0]

julia> A # A[1] et A[2] sont le même vecteur
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
