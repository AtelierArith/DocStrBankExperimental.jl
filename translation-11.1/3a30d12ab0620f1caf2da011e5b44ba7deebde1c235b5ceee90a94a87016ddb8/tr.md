```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

`n`'nin modüler tersini `T` türündeki tam sayı halkasında hesaplar, yani `2^N` modunda, burada `N = 8*sizeof(T)` (örneğin `N = 32` için `Int32`). Başka bir deyişle, bu yöntemler aşağıdaki kimlikleri sağlar:

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

Burada `*` modüler çarpma anlamına gelir, `T` tam sayı halkasında.

Bir tam sayı türü tarafından ima edilen modülü açık bir değer olarak belirtmek genellikle elverişsizdir çünkü modül tanım gereği tür tarafından temsil edilemeyecek kadar büyüktür.

Modüler ters, genel duruma göre çok daha verimli bir şekilde, https://arxiv.org/pdf/2204.04342.pdf adresinde açıklanan algoritma kullanılarak hesaplanır.

!!! compat "Julia 1.11"
    `invmod(n)` ve `invmod(n, T)` yöntemleri Julia 1.11 veya daha yenisini gerektirir.

