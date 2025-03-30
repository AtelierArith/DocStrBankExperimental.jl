```
@coalesce(x...)
```

Kısa devre versiyonu [`coalesce`](@ref).

# Örnekler

```jldoctest
julia> f(x) = (println("f($x)"); missing);

julia> a = 1;

julia> a = @coalesce a f(2) f(3) error("`a` hala eksik")
1

julia> b = missing;

julia> b = @coalesce b f(2) f(3) error("`b` hala eksik")
f(2)
f(3)
HATA: `b` hala eksik
[...]
```

!!! compat "Julia 1.7"
    Bu makro Julia 1.7 itibarıyla mevcuttur.

