```
Union{}
```

`Union{}`, boş [`Union`](@ref) türlerin, değer içermeyen türdür. Yani, `isa(x, Union{}) == false` tanımlayıcı özelliğine sahiptir her `x` için. `Base.Bottom`, onun takma adı olarak tanımlanmıştır ve `Union{}` türünün `Core.TypeofBottom` olduğu belirtilmiştir.

# Örnekler

```jldoctest
julia> isa(nothing, Union{})
false
```
