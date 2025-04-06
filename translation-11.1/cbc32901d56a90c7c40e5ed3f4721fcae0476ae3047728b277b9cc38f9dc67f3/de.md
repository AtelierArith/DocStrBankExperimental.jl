```
IdDict([itr])
```

`IdDict{K,V}()` konstruiert eine Hash-Tabelle unter Verwendung von [`objectid`](@ref) als Hash und `===` als Gleichheit mit Schlüsseln vom Typ `K` und Werten vom Typ `V`. Siehe [`Dict`](@ref) für weitere Hilfe und [`IdSet`](@ref) für die Set-Version davon.

Im folgenden Beispiel sind die `Dict`-Schlüssel alle `isequal` und werden daher gleich gehasht, sodass sie überschrieben werden. Das `IdDict` hasht nach Objekt-ID und bewahrt somit die 3 verschiedenen Schlüssel.

# Beispiele

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} mit 1 Eintrag:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} mit 3 Einträgen:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
