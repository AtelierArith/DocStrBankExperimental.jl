```
isless(a::AbstractString, b::AbstractString) -> Bool
```

Dize `a` dize `b`'den alfabetik sırada (teknik olarak, Unicode kod noktalarına göre leksikografik sırada) önce gelip gelmediğini test eder.

# Örnekler

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
