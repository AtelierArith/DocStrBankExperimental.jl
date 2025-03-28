```
@locals()
```

Construye un diccionario de los nombres (como símbolos) y valores de todas las variables locales definidas en el sitio de llamada.

!!! compat "Julia 1.1"
    Este macro requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> let x = 1, y = 2
           Base.@locals
       end
Dict{Symbol, Any} con 2 entradas:
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
