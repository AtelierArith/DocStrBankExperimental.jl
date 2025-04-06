```
merge(d::AbstractDict, others::AbstractDict...)
```

Konstruiere eine zusammengeführte Sammlung aus den gegebenen Sammlungen. Falls notwendig, werden die Typen der resultierenden Sammlung angehoben, um die Typen der zusammengeführten Sammlungen zu berücksichtigen. Wenn der gleiche Schlüssel in einer anderen Sammlung vorhanden ist, wird der Wert für diesen Schlüssel der Wert sein, den er in der letzten aufgelisteten Sammlung hat. Siehe auch [`mergewith`](@ref) für eine benutzerdefinierte Handhabung von Werten mit dem gleichen Schlüssel.

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

julia> merge(a, b)
Dict{String, Float64} mit 3 Einträgen:
  "bar" => 4711.0
  "baz" => 17.0
  "foo" => 0.0

julia> merge(b, a)
Dict{String, Float64} mit 3 Einträgen:
  "bar" => 42.0
  "baz" => 17.0
  "foo" => 0.0
```
