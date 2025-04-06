```
Symbol(x...) -> Symbol
```

Argümanların string temsillerini birleştirerek bir [`Symbol`](@ref) oluşturur.

# Örnekler

```jldoctest
julia> Symbol("my", "name")
:myname

julia> Symbol("day", 4)
:day4
```
