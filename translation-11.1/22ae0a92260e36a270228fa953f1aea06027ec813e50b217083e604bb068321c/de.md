```
reduce(op, itr; [init])
```

Reduzieren Sie die gegebene Sammlung `itr` mit dem gegebenen binären Operator `op`. Wenn angegeben, muss der Anfangswert `init` ein neutrales Element für `op` sein, das für leere Sammlungen zurückgegeben wird. Es ist nicht spezifiziert, ob `init` für nicht-leere Sammlungen verwendet wird.

Für leere Sammlungen ist die Bereitstellung von `init` notwendig, außer in einigen Sonderfällen (z. B. wenn `op` einer von `+`, `*`, `max`, `min`, `&`, `|` ist), wenn Julia das neutrale Element von `op` bestimmen kann.

Reduktionen für bestimmte häufig verwendete Operatoren können spezielle Implementierungen haben und sollten stattdessen verwendet werden: [`maximum`](@ref)`(itr)`, [`minimum`](@ref)`(itr)`, [`sum`](@ref)`(itr)`, [`prod`](@ref)`(itr)`, [`any`](@ref)`(itr)`, [`all`](@ref)`(itr)`. Es gibt effiziente Methoden zum Verketten bestimmter Arrays von Arrays, indem Sie `reduce(`[`vcat`](@ref)`, arr)` oder `reduce(`[`hcat`](@ref)`, arr)` aufrufen.

Die Assoziativität der Reduktion ist implementationsabhängig. Das bedeutet, dass Sie nicht-assoziative Operationen wie `-` nicht verwenden können, da nicht definiert ist, ob `reduce(-,[1,2,3])` als `(1-2)-3` oder `1-(2-3)` ausgewertet werden sollte. Verwenden Sie stattdessen [`foldl`](@ref) oder [`foldr`](@ref) für garantierte linke oder rechte Assoziativität.

Einige Operationen akkumulieren Fehler. Parallelität wird einfacher, wenn die Reduktion in Gruppen ausgeführt werden kann. Zukünftige Versionen von Julia könnten den Algorithmus ändern. Beachten Sie, dass die Elemente nicht neu angeordnet werden, wenn Sie eine geordnete Sammlung verwenden.

# Beispiele

```jldoctest
julia> reduce(*, [2; 3; 4])
24

julia> reduce(*, [2; 3; 4]; init=-1)
-24
```
