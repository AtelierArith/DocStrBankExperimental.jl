```
cmp(x,y)
```

`x`'in `y`'den küçük, eşit veya büyük olup olmadığına bağlı olarak sırasıyla -1, 0 veya 1 döner. `isless` tarafından uygulanan toplam sıralamayı kullanır.

# Örnekler

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
HATA: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
