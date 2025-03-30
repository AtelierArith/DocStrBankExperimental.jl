```
uuid4([rng::AbstractRNG]) -> UUID
```

RFC 4122'de belirtildiği gibi, versiyon 4 (rastgele veya sahte rastgele) evrensel benzersiz tanımlayıcı (UUID) oluşturur.

`uuid4` tarafından kullanılan varsayılan rng `Random.default_rng()` değildir ve bir argüman olmadan her `uuid4()` çağrısının benzersiz bir tanımlayıcı döndürmesi beklenmelidir. Önemli olarak, `uuid4`'ün çıktıları, `Random.seed!(seed)` çağrıldığında bile tekrarlamaz. Şu anda (Julia 1.6 itibarıyla), `uuid4` varsayılan rng olarak `Random.RandomDevice` kullanmaktadır. Ancak, bu gelecekte değişebilecek bir uygulama ayrıntısıdır.

!!! compat "Julia 1.6"
    `uuid4`'ün çıktısı, Julia 1.6 itibarıyla `Random.default_rng()`'e bağlı değildir.


# Örnekler

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```
