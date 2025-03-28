```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

Créez un objet itérable pour visiter chaque index d'un `AbstractArray` `A` de manière efficace. Pour les types de tableau qui ont opté pour un indexation linéaire rapide (comme `Array`), c'est simplement l'intervalle `1:length(A)` s'ils utilisent une indexation basée sur 1. Pour les types de tableau qui n'ont pas opté pour une indexation linéaire rapide, un intervalle cartésien spécialisé est généralement renvoyé pour indexer efficacement le tableau avec des indices spécifiés pour chaque dimension.

En général, `eachindex` accepte des itérables arbitraires, y compris des chaînes de caractères et des dictionnaires, et renvoie un objet itérateur prenant en charge des types d'index arbitraires (par exemple, des indices non uniformément espacés ou non entiers).

Si `A` est `AbstractArray`, il est possible de spécifier explicitement le style des indices qui doivent être renvoyés par `eachindex` en passant une valeur ayant le type `IndexStyle` comme premier argument (typiquement `IndexLinear()` si des indices linéaires sont requis ou `IndexCartesian()` si un intervalle cartésien est souhaité).

Si vous fournissez plus d'un argument `AbstractArray`, `eachindex` créera un objet itérable qui est rapide pour tous les arguments (typiquement un [`UnitRange`](@ref) si toutes les entrées ont une indexation linéaire rapide, un [`CartesianIndices`](@ref) sinon). Si les tableaux ont des tailles et/ou des dimensions différentes, une exception `DimensionMismatch` sera levée.

Voir aussi [`pairs`](@ref)`(A)` pour itérer sur les indices et les valeurs ensemble, et [`axes`](@ref)`(A, 2)` pour des indices valides le long d'une dimension.

# Exemples

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # indexation linéaire
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # indexation cartésienne
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
