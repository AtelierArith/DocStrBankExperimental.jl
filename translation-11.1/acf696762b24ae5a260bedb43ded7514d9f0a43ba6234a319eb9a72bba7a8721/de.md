```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

Konstruiere eine zusammengeführte Sammlung aus den gegebenen Sammlungen. Falls notwendig, werden die Typen der resultierenden Sammlung angehoben, um die Typen der zusammengeführten Sammlungen zu berücksichtigen. Werte mit demselben Schlüssel werden mithilfe der Kombinationsfunktion kombiniert. Die curried Form `mergewith(combine)` gibt die Funktion `(args...) -> mergewith(combine, args...)` zurück.

Die Methode `merge(combine::Union{Function,Type}, args...)` als Alias von `mergewith(combine, args...)` ist weiterhin verfügbar für die Abwärtskompatibilität.

!!! compat "Julia 1.5"
    `mergewith` erfordert Julia 1.5 oder später.


# Beispiele

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} mit 2 Einträgen:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} mit 2 Einträgen:
  "bar" => 4711
  "baz" => 17

julia> mergewith(+, a, b)
Dict{String, Float64} mit 3 Einträgen:
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
