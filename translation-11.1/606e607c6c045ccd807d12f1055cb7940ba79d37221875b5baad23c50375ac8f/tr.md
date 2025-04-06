```
ncodeunits(s::AbstractString) -> Int
```

Bir dizedeki kod birimlerinin sayısını döndürür. Bu dizeye erişmek için geçerli olan indeksler `1 ≤ i ≤ ncodeunits(s)` koşulunu sağlamalıdır. Tüm bu indeksler geçerli olmayabilir – bir karakterin başlangıcı olmayabilirler, ancak `codeunit(s,i)` çağrıldığında bir kod birimi değeri döndüreceklerdir.

# Örnekler

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

Ayrıca [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref) bakınız.
