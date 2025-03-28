```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

Construit un objet [`Ordering`](@ref) à partir des mêmes arguments utilisés par [`sort!`](@ref). Les éléments sont d'abord transformés par la fonction `by` (qui peut être [`identity`](@ref)) et sont ensuite comparés selon la fonction `lt` ou un ordre existant `order`. `lt` doit être [`isless`](@ref) ou une fonction qui respecte les mêmes règles que le paramètre `lt` de [`sort!`](@ref). Enfin, l'ordre résultant est inversé si `rev=true`.

Passer un `lt` autre que `isless` avec un `order` autre que [`Base.Order.Forward`](@ref) ou [`Base.Order.Reverse`](@ref) n'est pas permis, sinon toutes les options sont indépendantes et peuvent être utilisées ensemble dans toutes les combinaisons possibles.
