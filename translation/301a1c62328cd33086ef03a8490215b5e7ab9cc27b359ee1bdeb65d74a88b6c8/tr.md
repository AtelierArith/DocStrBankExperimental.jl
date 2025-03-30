```
istaskfailed(t::Task) -> Bool
```

Bir görevin bir istisna atıldığı için çıkıp çıkmadığını belirleyin.

# Örnekler

```jldoctest
julia> a4() = error("görev başarısız");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

