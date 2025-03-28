```
@locals()
```

Construit un dictionnaire des noms (sous forme de symboles) et des valeurs de toutes les variables locales définies au moment de l'appel.

!!! compat "Julia 1.1"
    Ce macro nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> let x = 1, y = 2
           Base.@locals
       end
Dict{Symbol, Any} avec 2 entrées :
  :y => 2
  :x => 1

julia> function f(x)
           local y
           show(Base.@locals); println()
           for i = 1:1
               show(Base.@locals); println()
           end
           y = 2
           show(Base.@locals); println()
           nothing
       end;

julia> f(42)
Dict{Symbol, Any}(:x => 42)
Dict{Symbol, Any}(:i => 1, :x => 42)
Dict{Symbol, Any}(:y => 2, :x => 42)
```
