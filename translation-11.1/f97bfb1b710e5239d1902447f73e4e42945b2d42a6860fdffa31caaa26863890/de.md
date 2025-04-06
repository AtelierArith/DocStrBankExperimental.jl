```
@locals()
```

Konstruiere ein Wörterbuch der Namen (als Symbole) und Werte aller lokalen Variablen, die zum Zeitpunkt des Aufrufs definiert sind.

!!! compat "Julia 1.1"
    Dieses Makro erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> let x = 1, y = 2
           Base.@locals
       end
Dict{Symbol, Any} mit 2 Einträgen:
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
