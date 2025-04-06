```
repeat(c::AbstractChar, r::Integer) -> String
```

Bir karakteri `r` kez tekrarlar. Bu, [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)) çağrılarak da eşdeğer şekilde gerçekleştirilebilir.

# Örnekler

```jldoctest
julia> repeat('A', 3)
"AAA"
```
