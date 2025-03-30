```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

`EnumName` adında bir `Enum{BaseType}` alt türü oluşturur ve `value1` ve `value2` enum üye değerleri ile isteğe bağlı olarak atanmış `x` ve `y` değerlerini içerir. `EnumName`, diğer türler gibi kullanılabilir ve enum üye değerleri, aşağıdaki gibi normal değerler olarak kullanılabilir.

# Örnekler

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "Ben bir değerim: $(Int(x)) olan bir Meyve'yim"
f (generic function with 1 method)

julia> f(apple)
"Ben bir değerim: 1 olan bir Meyve'yim"

julia> Fruit(1)
apple::Fruit = 1
```

Değerler ayrıca bir `begin` bloğu içinde de belirtilebilir, örneğin:

```julia
@enum EnumName begin
    value1
    value2
end
```

Varsayılan olarak [`Int32`](@ref) olan `BaseType`, `Integer`'ın bir ilkel alt türü olmalıdır. Üye değerleri, enum türü ile `BaseType` arasında dönüştürülebilir. `read` ve `write` bu dönüşümleri otomatik olarak gerçekleştirir. Enum, varsayılan olmayan bir `BaseType` ile oluşturulursa, `Integer(value1)` `value1` tam sayısını `BaseType` türü ile döndürecektir.

Bir enum'un tüm örneklerini listelemek için `instances` kullanın, örneğin:

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

Bir enum örneğinden bir sembol oluşturmak mümkündür:

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
