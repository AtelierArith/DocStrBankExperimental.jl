```
für outer
```

Wiederverwenden einer vorhandenen lokalen Variablen für die Iteration in einer `for`-Schleife.

Siehe den [Handbuchabschnitt über Variablenbereich](@ref scope-of-variables) für weitere Informationen.

Siehe auch [`for`](@ref).

# Beispiele

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # leer
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # leer
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # globale Variable
       for outer i = 1:3
       end
ERROR: Syntax: keine äußere lokale Variablendeklaration für "for outer" vorhanden
[...]
```
