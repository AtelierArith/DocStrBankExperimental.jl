```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Trie le vecteur `v` sur place. Un algorithme stable est utilisé par défaut : l'ordre des éléments qui se comparent comme égaux est préservé. Un algorithme spécifique peut être sélectionné via le mot-clé `alg` (voir [Algorithmes de tri](@ref) pour les algorithmes disponibles).

Les éléments sont d'abord transformés avec la fonction `by` puis comparés selon la fonction `lt` ou l'ordre `order`. Enfin, l'ordre résultant est inversé si `rev=true` (cela préserve la stabilité en avant : les éléments qui se comparent comme égaux ne sont pas inversés). L'implémentation actuelle applique la transformation `by` avant chaque comparaison plutôt qu'une fois par élément.

Passer un `lt` autre que `isless` avec un `order` autre que [`Base.Order.Forward`](@ref) ou [`Base.Order.Reverse`](@ref) n'est pas permis, sinon toutes les options sont indépendantes et peuvent être utilisées ensemble dans toutes les combinaisons possibles. Notez que `order` peut également inclure une transformation "by", auquel cas elle est appliquée après celle définie avec le mot-clé `by`. Pour plus d'informations sur les valeurs `order`, voir la documentation sur [Ordres alternatifs](@ref).

Les relations entre deux éléments sont définies comme suit (avec "moins" et "plus" échangés lorsque `rev=true`) :

  * `x` est inférieur à `y` si `lt(by(x), by(y))` (ou `Base.Order.lt(order, by(x), by(y))`) renvoie vrai.
  * `x` est supérieur à `y` si `y` est inférieur à `x`.
  * `x` et `y` sont équivalents si aucun n'est inférieur à l'autre ("incomparable" est parfois utilisé comme synonyme d'"équivalent").

Le résultat de `sort!` est trié dans le sens où chaque élément est supérieur ou équivalent au précédent.

La fonction `lt` doit définir un ordre faible strict, c'est-à-dire qu'elle doit être

  * irréflexive : `lt(x, x)` renvoie toujours `false`,
  * asymétrique : si `lt(x, y)` renvoie `true`, alors `lt(y, x)` renvoie `false`,
  * transitive : `lt(x, y) && lt(y, z)` implique `lt(x, z)`,
  * transitive en équivalence : `!lt(x, y) && !lt(y, x)` et `!lt(y, z) && !lt(z, y)` ensemble impliquent `!lt(x, z) && !lt(z, x)`. En d'autres termes : si `x` et `y` sont équivalents et `y` et `z` sont équivalents, alors `x` et `z` doivent être équivalents.

Par exemple, `<` est une fonction `lt` valide pour les valeurs `Int`, mais `≤` ne l'est pas : elle viole l'irréflexivité. Pour les valeurs `Float64`, même `<` est invalide car elle viole la quatrième condition : `1.0` et `NaN` sont équivalents et il en va de même pour `NaN` et `2.0`, mais `1.0` et `2.0` ne sont pas équivalents.

Voir aussi [`sort`](@ref), [`sortperm`](@ref), [`sortslices`](@ref), [`partialsort!`](@ref), [`partialsortperm`](@ref), [`issorted`](@ref), [`searchsorted`](@ref), [`insorted`](@ref), [`Base.Order.ord`](@ref).

# Exemples

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # même que sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # tri correct avec lt par défaut=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # tri incorrect en raison d'un lt invalide. Ce comportement est indéfini.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
