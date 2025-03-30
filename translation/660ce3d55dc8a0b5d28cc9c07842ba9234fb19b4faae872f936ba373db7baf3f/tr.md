```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Bir koleksiyonun sıralı olup olmadığını test eder. Anahtar kelimeler, sıralı olarak kabul edilen sıralamayı değiştirebilir; bu, [`sort!`](@ref) belgelerinde açıklanmıştır.

# Örnekler

```jldoctest
julia> issorted([1, 2, 3])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
false

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
true

julia> issorted([1, 2, -2, 3], by=abs)
true
```
