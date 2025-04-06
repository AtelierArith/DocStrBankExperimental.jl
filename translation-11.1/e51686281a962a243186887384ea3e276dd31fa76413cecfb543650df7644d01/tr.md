```
isa(x, type) -> Bool
```

`x`'in verilen `type` türünde olup olmadığını belirler. Ayrıca infiks operatör olarak da kullanılabilir, örneğin `x isa type`.

# Örnekler

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, Matrix)
false

julia> isa(1, Char)
false

julia> isa(1, Number)
true

julia> 1 isa Number
true
```
