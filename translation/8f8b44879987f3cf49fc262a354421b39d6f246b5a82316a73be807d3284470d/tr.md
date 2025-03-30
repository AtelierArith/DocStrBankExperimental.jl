```
which(f, types)
```

Verilen `types` argümanları için çağrılacak `f`'nin (bir `Method` nesnesi) yöntemini döndürür.

Eğer `types` soyut bir türse, o zaman `invoke` tarafından çağrılacak yöntem döndürülür.

Ayrıca bakınız: [`parentmodule`](@ref), [`@which`](@ref Main.InteractiveUtils.@which), ve [`@edit`](@ref Main.InteractiveUtils.@edit).
