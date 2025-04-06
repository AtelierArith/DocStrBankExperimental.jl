```
to_indices(A, I::Tuple)
```

Convertir le tuple `I` en un tuple d'indices à utiliser pour indexer le tableau `A`.

Le tuple retourné ne doit contenir que des `Int`s ou des `AbstractArray`s d'indices scalaires qui sont supportés par le tableau `A`. Il renverra une erreur en rencontrant un type d'index nouveau qu'il ne sait pas traiter.

Pour les types d'index simples, il se réfère à la fonction non exportée `Base.to_index(A, i)` pour traiter chaque index `i`. Bien que cette fonction interne ne soit pas destinée à être appelée directement, `Base.to_index` peut être étendue par des types de tableaux ou d'index personnalisés pour fournir des comportements d'indexation personnalisés.

Des types d'index plus compliqués peuvent nécessiter plus de contexte sur la dimension dans laquelle ils indexent. Pour prendre en charge ces cas, `to_indices(A, I)` appelle `to_indices(A, axes(A), I)`, qui parcourt ensuite de manière récursive à la fois le tuple donné d'indices et les indices dimensionnels de `A` en tandem. Ainsi, tous les types d'index ne sont pas garantis de se propager à `Base.to_index`.

# Exemples

```jldoctest
julia> A = zeros(1,2,3,4);

julia> to_indices(A, (1,1,2,2))
(1, 1, 2, 2)

julia> to_indices(A, (1,1,2,20)) # pas de vérification des limites
(1, 1, 2, 20)

julia> to_indices(A, (CartesianIndex((1,)), 2, CartesianIndex((3,4)))) # index exotique
(1, 2, 3, 4)

julia> to_indices(A, ([1,1], 1:2, 3, 4))
([1, 1], 1:2, 3, 4)

julia> to_indices(A, (1,2)) # pas de vérification de forme
(1, 2)
```
