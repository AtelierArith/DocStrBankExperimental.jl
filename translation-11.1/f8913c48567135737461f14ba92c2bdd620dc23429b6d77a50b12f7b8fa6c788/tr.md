```
to_indices(A, I::Tuple)
```

Dizi `A`'ya indeksleme için `I` tuple'ını indekslerin bir tuple'ına dönüştürür.

Dönen tuple yalnızca `A` dizisi tarafından desteklenen `Int` veya skalar indekslerin `AbstractArray`'larını içermelidir. İşlenemeyen yeni bir indeks türü ile karşılaştığında hata verecektir.

Basit indeks türleri için, her bir indeks `i`'yi işlemek üzere dışa aktarılmamış `Base.to_index(A, i)` fonksiyonuna başvurur. Bu iç fonksiyon doğrudan çağrılmak üzere tasarlanmamıştır, ancak `Base.to_index`, özel dizi veya indeks türleri tarafından özel indeksleme davranışları sağlamak için genişletilebilir.

Daha karmaşık indeks türleri, hangi boyuta indeksleme yaptıkları hakkında daha fazla bağlama ihtiyaç duyabilir. Bu tür durumları desteklemek için, `to_indices(A, I)` `to_indices(A, axes(A), I)` fonksiyonunu çağırır; bu da verilen indeks tuple'ı ile `A`'nın boyutsal indekslerini birlikte yinelemeli olarak dolaşır. Bu nedenle, tüm indeks türlerinin `Base.to_index`'e geçiş yapacağı garanti edilmez.

# Örnekler

```jldoctest
julia> A = zeros(1,2,3,4);

julia> to_indices(A, (1,1,2,2))
(1, 1, 2, 2)

julia> to_indices(A, (1,1,2,20)) # sınır kontrolü yok
(1, 1, 2, 20)

julia> to_indices(A, (CartesianIndex((1,)), 2, CartesianIndex((3,4)))) # egzotik indeks
(1, 2, 3, 4)

julia> to_indices(A, ([1,1], 1:2, 3, 4))
([1, 1], 1:2, 3, 4)

julia> to_indices(A, (1,2)) # şekil kontrolü yok
(1, 2)
```
