```
istaskstarted(t::Task) -> Bool
```

Bir görevin çalışmaya başlayıp başlamadığını belirleyin.

# Örnekler

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
