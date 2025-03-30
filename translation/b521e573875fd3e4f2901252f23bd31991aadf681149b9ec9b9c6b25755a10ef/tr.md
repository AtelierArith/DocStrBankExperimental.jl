```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

`pattern` için `string` içinde eşleşme sayısını döndürür. Bu, `length(findall(pattern, string))` çağrısına eşdeğerdir ancak daha verimlidir.

Eğer `overlap=true` ise, eşleşen diziler orijinal string içinde indeksleri örtüşecek şekilde izin verilir, aksi takdirde ayrı karakter aralıklarından olmalıdır.

!!! compat "Julia 1.3"
    Bu yöntem en az Julia 1.3 gerektirir.


!!! compat "Julia 1.7"
    Bir karakterin desen olarak kullanılması en az Julia 1.7 gerektirir.


# Örnekler

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
