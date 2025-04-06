```
für
```

`for`-Schleifen bewerten wiederholt einen Block von Anweisungen, während sie über eine Sequenz von Werten iterieren.

Die Iterationsvariable ist immer eine neue Variable, selbst wenn eine Variable mit demselben Namen im umgebenden Gültigkeitsbereich existiert. Verwenden Sie [`outer`](@ref), um eine vorhandene lokale Variable für die Iteration wiederzuverwenden.

# Beispiele

```jldoctest
julia> for i in [1, 4, 0]
           println(i)
       end
1
4
0
```
