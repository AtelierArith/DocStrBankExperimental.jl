```
^(x, y)
```

Opérateur d'exponentiation.

Si `x` et `y` sont des entiers, le résultat peut débordement. Pour entrer des nombres en notation scientifique, utilisez des littéraux [`Float64`](@ref) tels que `1.2e3` plutôt que `1.2 * 10^3`.

Si `y` est un littéral `Int` (par exemple `2` dans `x^2` ou `-3` dans `x^-3`), le code Julia `x^y` est transformé par le compilateur en `Base.literal_pow(^, x, Val(y))`, pour permettre une spécialisation à la compilation sur la valeur de l'exposant. (En tant que solution de secours par défaut, nous avons `Base.literal_pow(^, x, Val(y)) = ^(x,y)`, où généralement `^ == Base.^` à moins que `^` n'ait été défini dans l'espace de noms appelant.) Si `y` est un littéral entier négatif, alors `Base.literal_pow` transforme l'opération en `inv(x)^-y` par défaut, où `-y` est positif.

Voir aussi [`exp2`](@ref), [`<<`](@ref).

# Exemples

```jldoctest
julia> 3^5
243

julia> 3^-1  # utilise Base.literal_pow
0.3333333333333333

julia> p = -1;

julia> 3^p
ERREUR : DomainError avec -1 :
Impossible d'élever un entier x à une puissance négative -1.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # débordement entier
false

julia> big(10)^19 == 1e19
true
```
