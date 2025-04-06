```
local
```

`local` führt eine neue lokale Variable ein. Siehe den [Handbuchabschnitt zur Variablenbereich](@ref scope-of-variables) für weitere Informationen.

# Beispiele

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # führt ein schleifenlokales x ein
               x = i
           end
           x
       end
foo (generische Funktion mit 1 Methode)

julia> foo(10)
0
```
