```
@raw_str -> String
```

Erstellen Sie einen Rohstring ohne Interpolation und Unescaping. Die Ausnahme ist, dass Anführungszeichen weiterhin escaped werden müssen. Rückwärtsschslashes escapen sowohl Anführungszeichen als auch andere Rückwärtsschslashes, jedoch nur, wenn eine Folge von Rückwärtsschslashes einem Anführungszeichen vorausgeht. Somit kodiert 2n Rückwärtsschslashes, gefolgt von einem Anführungszeichen, n Rückwärtsschslashes und das Ende des Literals, während 2n+1 Rückwärtsschslashes, gefolgt von einem Anführungszeichen, n Rückwärtsschslashes, gefolgt von einem Anführungszeichen, kodiert.

# Beispiele

```jldoctest
julia> println(raw"\ $x")
\ $x

julia> println(raw"\"")
"

julia> println(raw"\\\"")
\"

julia> println(raw"\\x \\\"")
\\x \"
```
