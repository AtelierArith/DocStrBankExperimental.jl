```
fetch(c::Channel)
```

İlk mevcut öğeyi `Channel`'dan (kaldırmadan) bekler ve döndürür. Not: `fetch`, bir tamponlanmamış (0-boyutlu) `Channel` üzerinde desteklenmez.

# Örnekler

Tamponlu kanal:

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # öğe kaldırılmaz
3-element Vector{Any}:
 1
 2
 3
```
