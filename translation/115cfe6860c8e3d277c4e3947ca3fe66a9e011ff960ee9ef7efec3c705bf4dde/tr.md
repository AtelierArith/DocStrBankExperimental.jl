```
uuid1([rng::AbstractRNG]) -> UUID
```

RFC 4122'de belirtildiği gibi, versiyon 1 (zaman tabanlı) evrensel benzersiz tanımlayıcı (UUID) oluşturur. Node ID'nin rastgele oluşturulduğunu (host'u tanımlamaz) ve RFC'nin 4.5. bölümüne göre olduğunu unutmayın.

`uuid1` tarafından kullanılan varsayılan rng, `Random.default_rng()` değildir ve bir argüman olmadan her `uuid1()` çağrısının benzersiz bir tanımlayıcı döndürmesi beklenmelidir. Önemli olarak, `uuid1`'in çıktıları, `Random.seed!(seed)` çağrıldığında bile tekrarlamaz. Şu anda (Julia 1.6 itibarıyla), `uuid1` varsayılan rng olarak `Random.RandomDevice` kullanmaktadır. Ancak, bu gelecekte değişebilecek bir uygulama ayrıntısıdır.

!!! compat "Julia 1.6"
    `uuid1`'in çıktısı, Julia 1.6 itibarıyla `Random.default_rng()`'e bağlı değildir.


# Örnekler

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```
