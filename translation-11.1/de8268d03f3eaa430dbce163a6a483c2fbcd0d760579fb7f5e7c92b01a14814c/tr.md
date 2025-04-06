```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

C standart kütüphanesinden `realloc` çağrısı yapın.

[`free`](@ref) ile ilgili belgelerdeki uyarıya bakın; bu işlemi yalnızca [`malloc`](@ref) ile başlangıçta elde edilen bellek üzerinde kullanın.
