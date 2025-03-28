```
filter(f, d::AbstractDict)
```

Gibt eine Kopie von `d` zurück, wobei Elemente entfernt werden, für die `f` `false` ist. Die Funktion `f` erhält `key=>value` Paare.

# Beispiele

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} mit 2 Einträgen:
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} mit 1 Eintrag:
  1 => "a"
```
