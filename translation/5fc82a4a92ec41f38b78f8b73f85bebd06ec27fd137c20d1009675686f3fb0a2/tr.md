```
eltype(type)
```

Verilen `type` türündeki bir koleksiyonu iterasyona tabi tutarak üretilen elemanların türünü belirler. Sözlük türleri için bu, bir `Pair{KeyType,ValType}` olacaktır. `eltype(x) = eltype(typeof(x))` tanımı, türler yerine örneklerin geçilebilmesi için kolaylık sağlamak amacıyla verilmiştir. Ancak, bir tür argümanı kabul eden form yeni türler için tanımlanmalıdır.

Ayrıca bakınız: [`keytype`](@ref), [`typeof`](@ref).

# Örnekler

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
