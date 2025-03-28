```
UndefKeywordError(var::Symbol)
```

Das erforderliche Schlüsselwortargument `var` wurde bei einem Funktionsaufruf nicht zugewiesen.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function my_func(;my_arg)
           return my_arg + 1
       end
my_func (generische Funktion mit 1 Methode)

julia> my_func()
FEHLER: UndefKeywordError: Schlüsselwortargument `my_arg` nicht zugewiesen
Stacktrace:
 [1] my_func() bei ./REPL[1]:2
 [2] oberste Ebene bei REPL[2]:1
```
