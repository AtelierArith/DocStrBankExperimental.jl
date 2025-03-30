```
get(f::Union{Function, Type}, collection, key)
```

Verilen anahtar için saklanan değeri döndürür, eğer anahtar için bir eşleme yoksa `f()` döndürür. Varsayılan değeri sözlükte saklamak için [`get!`](@ref) kullanın.

Bu, `do` blok sözdizimi kullanılarak çağrılması amaçlanmıştır.

```julia
get(dict, key) do
    # varsayılan değer burada hesaplanır
    time()
end
```
