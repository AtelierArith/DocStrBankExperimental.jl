```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

Erstellt einen `Enum{BaseType}`-Untertyp mit dem Namen `EnumName` und den Enum-Mitgliedswerten `value1` und `value2` mit optional zugewiesenen Werten `x` und `y`. `EnumName` kann wie andere Typen verwendet werden und Enum-Mitgliedswerte als reguläre Werte, wie zum Beispiel

# Beispiele

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "Ich bin ein Fruit mit dem Wert: $(Int(x))"
f (generische Funktion mit 1 Methode)

julia> f(apple)
"Ich bin ein Fruit mit dem Wert: 1"

julia> Fruit(1)
apple::Fruit = 1
```

Werte können auch innerhalb eines `begin`-Blocks angegeben werden, z.B.

```julia
@enum EnumName begin
    value1
    value2
end
```

`BaseType`, das standardmäßig [`Int32`](@ref) ist, muss ein primitiver Untertyp von `Integer` sein. Mitgliedswerte können zwischen dem Enum-Typ und `BaseType` konvertiert werden. `read` und `write` führen diese Konvertierungen automatisch durch. Falls das Enum mit einem nicht standardmäßigen `BaseType` erstellt wird, gibt `Integer(value1)` den ganzzahligen `value1` mit dem Typ `BaseType` zurück.

Um alle Instanzen eines Enums aufzulisten, verwenden Sie `instances`, z.B.

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

Es ist möglich, ein Symbol aus einer Enum-Instanz zu konstruieren:

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
