```
reduce(op, itr; [init])
```

Réduit la collection donnée `itr` avec l'opérateur binaire donné `op`. Si fourni, la valeur initiale `init` doit être un élément neutre pour `op` qui sera retourné pour les collections vides. Il n'est pas spécifié si `init` est utilisé pour les collections non vides.

Pour les collections vides, fournir `init` sera nécessaire, sauf dans certains cas spéciaux (par exemple, lorsque `op` est l'un de `+`, `*`, `max`, `min`, `&`, `|`) lorsque Julia peut déterminer l'élément neutre de `op`.

Les réductions pour certains opérateurs couramment utilisés peuvent avoir des implémentations spéciales et doivent être utilisées à la place : [`maximum`](@ref)`(itr)`, [`minimum`](@ref)`(itr)`, [`sum`](@ref)`(itr)`, [`prod`](@ref)`(itr)`, [`any`](@ref)`(itr)`, [`all`](@ref)`(itr)`. Il existe des méthodes efficaces pour concaténer certains tableaux de tableaux en appelant `reduce(`[`vcat`](@ref)`, arr)` ou `reduce(`[`hcat`](@ref)`, arr)`.

L'associativité de la réduction dépend de l'implémentation. Cela signifie que vous ne pouvez pas utiliser des opérations non associatives comme `-` car il est indéfini si `reduce(-,[1,2,3])` doit être évalué comme `(1-2)-3` ou `1-(2-3)`. Utilisez [`foldl`](@ref) ou [`foldr`](@ref) à la place pour garantir l'associativité à gauche ou à droite.

Certaines opérations accumulent des erreurs. Le parallélisme sera plus facile si la réduction peut être exécutée par groupes. Les futures versions de Julia pourraient changer l'algorithme. Notez que les éléments ne sont pas réordonnés si vous utilisez une collection ordonnée.

# Exemples

```jldoctest
julia> reduce(*, [2; 3; 4])
24

julia> reduce(*, [2; 3; 4]; init=-1)
-24
```
