```
@inferred [AllowedType] f(x)
```

Çağrı ifadesinin `f(x)` derleyici tarafından çıkarılan aynı türde bir değer döndürdüğünü test eder. Tür kararlılığını kontrol etmek için yararlıdır.

`f(x)` herhangi bir çağrı ifadesi olabilir. Türler eşleşirse `f(x)`'in sonucunu döndürür ve farklı türler bulursa bir `Hata` `Sonucu` döndürür.

İsteğe bağlı olarak, `AllowedType` testi gevşetir; bu, `f(x)`'in türü çıkarılan türle `AllowedType` modülünde eşleştiğinde veya dönen tür `AllowedType`'in bir alt türü olduğunda geçmesini sağlar. Bu, `Union{Nothing, T}` veya `Union{Missing, T}` gibi küçük bir birleşim döndüren fonksiyonların tür kararlılığını test ederken yararlıdır.

```jldoctest; setup = :(using InteractiveUtils; using Base: >), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generic function with 1 method)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance for f(::Int64)
  from f(a) @ Main none:1
Arguments
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
HATA: dönüş türü Int64 çıkarılan dönüş türü Union{Float64, Int64} ile eşleşmiyor
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
HATA: dönüş türü Float64 çıkarılan dönüş türü Union{Missing, Float64} ile eşleşmiyor
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
HATA: dönüş türü Int64 çıkarılan dönüş türü Union{Missing, Float64, Int64} ile eşleşmiyor
[...]
```
