```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

`pattern`'ın `string` içinde `start` konumundan itibaren bir sonraki geçişini bulur. `pattern` bir dize veya bir düzenli ifade olabilir; bu durumda `string` `String` türünde olmalıdır.

Dönüş değeri, eşleşen dizinin bulunduğu indekslerin bir aralığıdır; böylece `s[findnext(x, s, i)] == x`:

`findnext("substring", string, i)` == `start:stop` böylece `string[start:stop] == "substring"` ve `i <= start`, veya eşleşmiyorsa `nothing`.

# Örnekler

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
