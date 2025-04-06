```
keys(m::RegexMatch) -> Vector
```

Gibt einen Vektor von Schlüsseln für alle Erfassungsgruppen des zugrunde liegenden regulären Ausdrucks zurück. Ein Schlüssel ist enthalten, auch wenn die Erfassungsgruppe nicht übereinstimmt. Das heißt, `idx` wird im Rückgabewert enthalten sein, auch wenn `m[idx] == nothing`.

Unbenannte Erfassungsgruppen haben ganzzahlige Schlüssel, die ihrem Index entsprechen. Benannte Erfassungsgruppen haben Zeichenfolgen-Schlüssel.

!!! compat "Julia 1.7"
    Diese Methode wurde in Julia 1.7 hinzugefügt


# Beispiele

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
