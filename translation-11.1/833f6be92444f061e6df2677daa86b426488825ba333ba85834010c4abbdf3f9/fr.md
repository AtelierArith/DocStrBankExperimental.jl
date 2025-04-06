# Bounds checking

Comme de nombreux langages de programmation modernes, Julia utilise la vérification des limites pour garantir la sécurité du programme lors de l'accès aux tableaux. Dans des boucles internes serrées ou d'autres situations critiques pour la performance, vous pouvez souhaiter ignorer ces vérifications de limites pour améliorer les performances d'exécution. Par exemple, afin d'émettre des instructions vectorisées (SIMD), le corps de votre boucle ne peut pas contenir de branches, et ne peut donc pas contenir de vérifications de limites. Par conséquent, Julia inclut un macro `@inbounds(...)` pour indiquer au compilateur d'ignorer ces vérifications de limites dans le bloc donné. Les types de tableaux définis par l'utilisateur peuvent utiliser le macro `@boundscheck(...)` pour réaliser une sélection de code sensible au contexte.

## Eliding bounds checks

Le macro `@boundscheck(...)` marque des blocs de code qui effectuent une vérification des limites. Lorsque de tels blocs sont intégrés dans un bloc `@inbounds(...)`, le compilateur peut supprimer ces blocs. Le compilateur supprime le bloc `@boundscheck` *uniquement s'il est intégré* dans la fonction appelante. Par exemple, vous pourriez écrire la méthode `sum` comme :

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

Avec un type personnalisé semblable à un tableau `MyArray` ayant :

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

Alors, lorsque `getindex` est intégré dans `sum`, l'appel à `checkbounds(A, i)` sera omis. Si votre fonction contient plusieurs niveaux d'inlining, seuls les blocs `@boundscheck` à un maximum d'un niveau d'inlining plus profond sont éliminés. La règle empêche les changements non intentionnels dans le comportement du programme provenant du code plus haut dans la pile.

### Caution!

Il est facile d'exposer accidentellement des opérations non sécurisées avec `@inbounds`. Vous pourriez être tenté d'écrire l'exemple ci-dessus comme

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

Ce qui suppose discrètement un indexage basé sur 1 et expose donc un accès mémoire non sécurisé lorsqu'il est utilisé avec [`OffsetArrays`](@ref man-custom-indices) :

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

Bien que la source originale de l'erreur ici soit `1:length(A)`, l'utilisation de `@inbounds` augmente les conséquences d'une erreur de limites à un accès mémoire non sécurisé, moins facilement détectable et débogable. Il est souvent difficile ou impossible de prouver qu'une méthode qui utilise `@inbounds` est sûre, il faut donc peser les avantages des améliorations de performance par rapport au risque de segfaults et de comportements silencieux incorrects, en particulier dans les API destinées au public.

## Propagating inbounds

Il peut y avoir certains scénarios où, pour des raisons d'organisation du code, vous souhaitez avoir plus d'une couche entre les déclarations `@inbounds` et `@boundscheck`. Par exemple, les méthodes par défaut `getindex` ont la chaîne `getindex(A::AbstractArray, i::Real)` appelle `getindex(IndexStyle(A), A, i)` appelle `_getindex(::IndexLinear, A, i)`.

Pour contourner la règle de "une couche d'inlining", une fonction peut être marquée avec [`Base.@propagate_inbounds`](@ref) pour propager un contexte inbounds (ou un contexte out of bounds) à travers une couche supplémentaire d'inlining.

## The bounds checking call hierarchy

La hiérarchie générale est :

  * `checkbounds(A, I...)` qui appelle

      * `checkbounds(Bool, A, I...)` qui appelle

          * `checkbounds_indices(Bool, axes(A), I)` qui appelle récursivement

              * `checkindex` pour chaque dimension

Ici `A` est le tableau, et `I` contient les indices "demandés". `axes(A)` renvoie un tuple des indices "permis" de `A`.

`checkbounds(A, I...)` génère une erreur si les indices sont invalides, tandis que `checkbounds(Bool, A, I...)` retourne `false` dans ce cas. `checkbounds_indices` rejette toute information sur le tableau autre que son tuple `axes`, et effectue une comparaison pure indices contre indices : cela permet à relativement peu de méthodes compilées de servir une énorme variété de types de tableaux. Les indices sont spécifiés sous forme de tuples, et sont généralement comparés de manière 1-1 avec des dimensions individuelles gérées en appelant une autre fonction importante, `checkindex` : typiquement,

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

donc `checkindex` vérifie une seule dimension. Toutes ces fonctions, y compris la fonction non exportée `checkbounds_indices`, ont des docstrings accessibles avec `?`.

Si vous devez personnaliser la vérification des limites pour un type de tableau spécifique, vous devez spécialiser `checkbounds(Bool, A, I...)`. Cependant, dans la plupart des cas, vous devriez pouvoir vous fier à `checkbounds_indices` tant que vous fournissez des `axes` utiles pour votre type de tableau.

Si vous avez des types d'index novateurs, envisagez d'abord de spécialiser `checkindex`, qui gère un seul index pour une dimension particulière d'un tableau. Si vous avez un type d'index multidimensionnel personnalisé (similaire à `CartesianIndex`), vous devrez peut-être envisager de spécialiser `checkbounds_indices`.

Notez que cette hiérarchie a été conçue pour réduire la probabilité d'ambiguïtés de méthode. Nous essayons de faire de `checkbounds` l'endroit où se spécialiser sur le type de tableau, et nous essayons d'éviter les spécialisations sur les types d'index ; inversement, `checkindex` est destiné à être spécialisé uniquement sur le type d'index (en particulier, le dernier argument).

## Emit bounds checks

Julia peut être lancé avec `--check-bounds={yes|no|auto}` pour émettre des vérifications de limites toujours, jamais, ou respecter les déclarations `@inbounds`.
