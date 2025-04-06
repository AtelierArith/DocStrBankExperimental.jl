```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

`pattern`'ın `string` içinde `start` konumundan başlayarak önceki bir örneğini bulur.

Dönüş değeri, eşleşen dizinin bulunduğu indekslerin bir aralığıdır; böylece `s[findprev(x, s, i)] == x`:

`findprev("substring", string, i)` == `start:stop` böylece `string[start:stop] == "substring"` ve `stop <= i`, veya eşleşme yoksa `nothing`.

# Örnekler

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
