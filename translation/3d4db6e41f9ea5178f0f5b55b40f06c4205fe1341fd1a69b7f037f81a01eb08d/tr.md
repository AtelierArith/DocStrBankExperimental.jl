```
count([f=identity,] itr; init=0) -> Integer
```

`itr` içinde `f` fonksiyonunun `true` döndürdüğü elemanların sayısını sayar. `f` atlandığında, `itr` içindeki `true` elemanların sayısını sayar (bu, boolean değerlerden oluşan bir koleksiyon olmalıdır). `init` isteğe bağlı olarak saymaya başlanacak değeri belirtir ve dolayısıyla çıktı türünü de belirler.

!!! compat "Julia 1.6"
    `init` anahtar kelimesi Julia 1.6'da eklendi.


Ayrıca bakınız: [`any`](@ref), [`sum`](@ref).

# Örnekler

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
