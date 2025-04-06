```
@something(x...)
```

[`something`](@ref) makrosunun kısa devre versiyonu.

# Örnekler

```jldoctest
julia> f(x) = (println("f($x)"); nothing);

julia> a = 1;

julia> a = @something a f(2) f(3) error("`a` için varsayılan bulunamadı")
1

julia> b = nothing;

julia> b = @something b f(2) f(3) error("`b` için varsayılan bulunamadı")
f(2)
f(3)
HATA: `b` için varsayılan bulunamadı
[...]

julia> b = @something b f(2) f(3) Some(nothing)
f(2)
f(3)

julia> b === nothing
true
```

!!! compat "Julia 1.7"
    Bu makro Julia 1.7 itibarıyla mevcuttur.

