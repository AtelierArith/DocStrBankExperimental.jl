```
Union{Types...}
```

Bir `Union` türü, argüman türlerinin herhangi birinin tüm örneklerini içeren soyut bir türdür. Bu, `T <: Union{T,S}` ve `S <: Union{T,S}` anlamına gelir.

Diğer soyut türler gibi, tüm argümanları soyut olmasa bile, örneklendirilemez.

# Örnekler

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # Int örneği birliğe dahil
true

julia> "Hello!" isa IntOrString # String de dahil
true

julia> 1.0 isa IntOrString # Float64 dahil değildir çünkü ne Int ne de AbstractString'dir
false
```

# Genişletilmiş Yardım

Çoğu diğer parametrik türün aksine, birleşimler parametrelerinde kovaryandır. Örneğin, `Union{Real, String}` bir alt türdur `Union{Number, AbstractString}`.

Boş birleşim [`Union{}`](@ref) Julia'nın en alt türüdür.
