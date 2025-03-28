```
ErrorException(msg)
```

Generischer Fehlertyp. Die Fehlermeldung im Feld `.msg` kann spezifischere Details liefern.

# Beispiele

```jldoctest
julia> ex = ErrorException("Ich habe etwas Schlechtes getan");

julia> ex.msg
"Ich habe etwas Schlechtes getan"
```
