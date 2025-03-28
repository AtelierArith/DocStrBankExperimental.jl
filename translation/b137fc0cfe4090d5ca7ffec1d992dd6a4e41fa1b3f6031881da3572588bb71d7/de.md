```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

Finde das vorherige Vorkommen von `pattern` in `string`, beginnend an der Position `start`.

Der Rückgabewert ist ein Bereich von Indizes, an dem die übereinstimmende Sequenz gefunden wird, sodass `s[findprev(x, s, i)] == x`:

`findprev("substring", string, i)` == `start:stop`, sodass `string[start:stop] == "substring"` und `stop <= i`, oder `nothing`, wenn keine Übereinstimmung gefunden wurde.

# Beispiele

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
