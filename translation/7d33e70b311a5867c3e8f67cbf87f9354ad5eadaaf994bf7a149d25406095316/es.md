```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

Crea un subtipo `Enum{BaseType}` con el nombre `EnumName` y valores de miembros de enumeración `value1` y `value2` con valores asignados opcionales de `x` y `y`, respectivamente. `EnumName` se puede usar como otros tipos y los valores de los miembros de enumeración como valores regulares, como

# Ejemplos

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "Soy una fruta con valor: $(Int(x))"
f (función genérica con 1 método)

julia> f(apple)
"Soy una fruta con valor: 1"

julia> Fruit(1)
apple::Fruit = 1
```

Los valores también se pueden especificar dentro de un bloque `begin`, por ejemplo:

```julia
@enum EnumName begin
    value1
    value2
end
```

`BaseType`, que por defecto es [`Int32`](@ref), debe ser un subtipo primitivo de `Integer`. Los valores de los miembros se pueden convertir entre el tipo de enumeración y `BaseType`. `read` y `write` realizan estas conversiones automáticamente. En caso de que la enumeración se cree con un `BaseType` no predeterminado, `Integer(value1)` devolverá el entero `value1` con el tipo `BaseType`.

Para listar todas las instancias de una enumeración, usa `instances`, por ejemplo:

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

Es posible construir un símbolo a partir de una instancia de enumeración:

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
