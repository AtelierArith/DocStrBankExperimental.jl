```
global
```

`global x` lässt `x` im aktuellen Gültigkeitsbereich und seinen inneren Gültigkeitsbereichen auf die globale Variable mit diesem Namen verweisen. Siehe den [Handbuchabschnitt über die Variablenbereich](@ref scope-of-variables) für weitere Informationen.

# Beispiele

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # verwende die z-Variable, die außerhalb von foo definiert ist
       end
foo (generische Funktion mit 1 Methode)

julia> foo()
6

julia> z
6
```
