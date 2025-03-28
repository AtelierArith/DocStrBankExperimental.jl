```
filter!(f, d::AbstractDict)
```

Aktualisiert `d`, indem Elemente entfernt werden, für die `f` `false` ist. Die Funktion `f` erhält `key=>value` Paare.

# Beispiele

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} mit 3 Einträgen:
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} mit 2 Einträgen:
  3 => "c"
  1 => "a"
```
