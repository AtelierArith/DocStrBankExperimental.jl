```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

Indica que una función de ordenamiento debe utilizar el algoritmo de ordenamiento rápido parcial. `PartialQuickSort(k)` es como `QuickSort`, pero solo se requiere encontrar y ordenar los elementos que terminarían en `v[k]` si `v` estuviera completamente ordenado.

Características:

  * *no estable*: no preserva el orden de los elementos que comparan como iguales (por ejemplo, "a" y "A" en un ordenamiento de letras que ignora mayúsculas y minúsculas).
  * *en el lugar* en memoria.
  * *divide y vencerás*: estrategia de ordenamiento similar a [`MergeSort`](@ref).

Ten en cuenta que `PartialQuickSort(k)` no necesariamente ordena todo el arreglo. Por ejemplo,

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```
