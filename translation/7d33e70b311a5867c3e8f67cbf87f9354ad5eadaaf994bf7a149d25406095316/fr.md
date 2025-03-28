```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

Créez un sous-type `Enum{BaseType}` avec le nom `EnumName` et des valeurs de membre d'énumération `value1` et `value2` avec des valeurs assignées optionnelles `x` et `y`, respectivement. `EnumName` peut être utilisé comme d'autres types et les valeurs de membre d'énumération comme des valeurs régulières, telles que

# Exemples

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "Je suis un Fruit avec la valeur : $(Int(x))"
f (fonction générique avec 1 méthode)

julia> f(apple)
"Je suis un Fruit avec la valeur : 1"

julia> Fruit(1)
apple::Fruit = 1
```

Les valeurs peuvent également être spécifiées à l'intérieur d'un bloc `begin`, par exemple

```julia
@enum EnumName begin
    value1
    value2
end
```

`BaseType`, qui par défaut est [`Int32`](@ref), doit être un sous-type primitif de `Integer`. Les valeurs de membre peuvent être converties entre le type d'énumération et `BaseType`. `read` et `write` effectuent ces conversions automatiquement. Dans le cas où l'énumération est créée avec un `BaseType` non par défaut, `Integer(value1)` renverra l'entier `value1` avec le type `BaseType`.

Pour lister toutes les instances d'une énumération, utilisez `instances`, par exemple

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

Il est possible de construire un symbole à partir d'une instance d'énumération :

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
