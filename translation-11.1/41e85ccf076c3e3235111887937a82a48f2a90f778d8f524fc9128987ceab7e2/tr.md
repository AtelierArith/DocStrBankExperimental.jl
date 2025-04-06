```
merge(d::AbstractDict, others::AbstractDict...)
```

Verilen koleksiyonlardan birleştirilmiş bir koleksiyon oluşturur. Gerekirse, sonuçta oluşan koleksiyonun türleri, birleştirilen koleksiyonların türlerini karşılamak için yükseltilecektir. Aynı anahtar başka bir koleksiyonda mevcutsa, o anahtar için değer, listelenen son koleksiyondaki değeri olacaktır. Aynı anahtara sahip değerlerin özel işlenmesi için [`mergewith`](@ref) kısmına da bakınız.

# Örnekler

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} with 2 entries:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} with 2 entries:
  "bar" => 4711
  "baz" => 17

julia> merge(a, b)
Dict{String, Float64} with 3 entries:
  "bar" => 4711.0
  "baz" => 17.0
  "foo" => 0.0

julia> merge(b, a)
Dict{String, Float64} with 3 entries:
  "bar" => 42.0
  "baz" => 17.0
  "foo" => 0.0
```
