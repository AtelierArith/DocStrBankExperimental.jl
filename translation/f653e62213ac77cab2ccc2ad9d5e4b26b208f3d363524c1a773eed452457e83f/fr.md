```
Char(c::Union{Number,AbstractChar})
```

`Char` est un type [`AbstractChar`](@ref) de 32 bits qui est la représentation par défaut des caractères dans Julia. `Char` est le type utilisé pour les littéraux de caractères comme `'x'` et c'est aussi le type d'élément de [`String`](@ref).

Pour représenter sans perte des flux d'octets arbitraires stockés dans un `String`, une valeur `Char` peut stocker des informations qui ne peuvent pas être converties en un point de code Unicode — convertir un tel `Char` en `UInt32` générera une erreur. La fonction [`isvalid(c::Char)`](@ref) peut être utilisée pour vérifier si `c` représente un caractère Unicode valide.
