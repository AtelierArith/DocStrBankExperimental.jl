```
hash(x[, h::UInt]) -> UInt
```

Bir tam sayı hash kodu hesaplayın, böylece `isequal(x,y)` ifadesi `hash(x)==hash(y)` anlamına gelir. İsteğe bağlı ikinci argüman `h`, sonuçla karıştırılacak başka bir hash kodudur.

Yeni türler, genellikle içeriklerin hash'lerini birbirleriyle (ve `h` ile) karıştırmak için 2-argümanlı `hash` yöntemini özyinelemeli olarak çağırarak 2-argümanlı biçimi uygulamalıdır. Genellikle, `hash` uygulayan herhangi bir tür, yukarıda belirtilen özelliği garanti etmek için kendi [`==`](@ref) (dolayısıyla [`isequal`](@ref)) yöntemini de uygulamalıdır.

Hash değeri, yeni bir Julia süreci başlatıldığında değişebilir.

```jldoctest
julia> a = hash(10)
0x95ea2955abd45275

julia> hash(10, a) # yalnızca başka bir hash fonksiyonunun çıktısını ikinci argüman olarak kullanın
0xd42bad54a8575b16
```

Ayrıca bkz: [`objectid`](@ref), [`Dict`](@ref), [`Set`](@ref).
