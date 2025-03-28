```
code_typed(f, types; kw...)
```

Renvoie un tableau de la forme abaissée (IR) inférée par type pour les méthodes correspondant à la fonction générique donnée et à la signature de type.

# Arguments Clés

  * `optimize::Bool = true`: optionnel, contrôle si des optimisations supplémentaires, telles que l'inlining, sont également appliquées.
  * `debuginfo::Symbol = :default`: optionnel, contrôle la quantité de métadonnées de code présentes dans la sortie, les options possibles sont `:source` ou `:none`.

# Arguments Clés Internes

Cette section doit être considérée comme interne, et est uniquement destinée à ceux qui comprennent les internals du compilateur Julia.

  * `world::UInt = Base.get_world_counter()`: optionnel, contrôle l'âge du monde à utiliser lors de la recherche de méthodes, utilise l'âge du monde actuel si non spécifié.
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`: optionnel, contrôle l'interpréteur abstrait à utiliser, utilise l'interpréteur natif si non spécifié.

# Exemples

On peut mettre les types d'arguments dans un tuple pour obtenir le `code_typed` correspondant.

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
