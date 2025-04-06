```
@nospecialize
```

Appliqué à un nom d'argument de fonction, cela indique au compilateur que l'implémentation de la méthode ne doit pas être spécialisée pour différents types de cet argument, mais plutôt utiliser le type déclaré pour cet argument. Il peut être appliqué à un argument dans une liste d'arguments formelle, ou dans le corps de la fonction. Lorsqu'il est appliqué à un argument, la macro doit envelopper l'ensemble de l'expression d'argument, par exemple, `@nospecialize(x::Real)` ou `@nospecialize(i::Integer...)` plutôt que d'envelopper seulement le nom de l'argument. Lorsqu'il est utilisé dans un corps de fonction, la macro doit se trouver en position de déclaration et avant tout code.

Lorsqu'il est utilisé sans arguments, il s'applique à tous les arguments de la portée parente. Dans une portée locale, cela signifie tous les arguments de la fonction contenant. Dans une portée globale (de niveau supérieur), cela signifie toutes les méthodes définies par la suite dans le module actuel.

La spécialisation peut être réinitialisée à la valeur par défaut en utilisant [`@specialize`](@ref).

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! note
    `@nospecialize` affecte la génération de code mais pas l'inférence : il limite la diversité du code natif résultant, mais n'impose aucune limitation (au-delà des normes) sur l'inférence de type. Utilisez [`Base.@nospecializeinfer`](@ref) avec `@nospecialize` pour supprimer également l'inférence.


# Exemples

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

Ici, l'annotation `@nospecialize` donne lieu à l'équivalent de

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

garantissant qu'une seule version de code natif sera générée pour `g`, une qui est générique pour tout `AbstractArray`. Cependant, le type de retour spécifique est toujours inféré pour `g` et `f`, et cela est toujours utilisé pour optimiser les appelants de `f` et `g`.
