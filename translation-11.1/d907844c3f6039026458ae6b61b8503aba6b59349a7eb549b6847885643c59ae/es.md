```
NamedTuple
```

Los `NamedTuple`s son, como su nombre sugiere, [`Tuple`](@ref)s nombrados. Es decir, son una colección de valores similar a una tupla, donde cada entrada tiene un nombre único, representado como un [`Symbol`](@ref). Al igual que los `Tuple`s, los `NamedTuple`s son inmutables; ni los nombres ni los valores pueden ser modificados en su lugar después de la construcción.

Un tuple nombrado se puede crear como un literal de tupla con claves, por ejemplo, `(a=1, b=2)`, o como un literal de tupla con un punto y coma después del paréntesis de apertura, por ejemplo, `(; a=1, b=2)` (esta forma también acepta nombres generados programáticamente como se describe a continuación), o utilizando un tipo `NamedTuple` como constructor, por ejemplo, `NamedTuple{(:a, :b)}((1,2))`.

Acceder al valor asociado con un nombre en un tuple nombrado se puede hacer utilizando la sintaxis de acceso a campos, por ejemplo, `x.a`, o utilizando [`getindex`](@ref), por ejemplo, `x[:a]` o `x[(:a, :b)]`. Un tuple de los nombres se puede obtener utilizando [`keys`](@ref), y un tuple de los valores se puede obtener utilizando [`values`](@ref).

!!! note
    La iteración sobre `NamedTuple`s produce los *valores* sin los nombres. (Ver ejemplo a continuación.) Para iterar sobre los pares nombre-valor, utiliza la función [`pairs`](@ref).


El macro [`@NamedTuple`](@ref) se puede usar para declarar convenientemente tipos `NamedTuple`.

# Ejemplos

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

De manera similar a cómo se pueden definir argumentos de palabra clave programáticamente, un tuple nombrado se puede crear dando pares `name::Symbol => value` después de un punto y coma dentro de un literal de tupla. Esta sintaxis y la sintaxis `name=value` se pueden mezclar:

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

Los pares nombre-valor también se pueden proporcionar desglosando un tuple nombrado o cualquier iterador que produzca colecciones de dos valores que contengan cada uno un símbolo como primer valor:

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # el último b sobrescribe el valor de nt1
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip produce tuplas como (:a, 1)
(a = 1, b = 2, c = 3)
```

Al igual que en los argumentos de palabra clave, los identificadores y las expresiones de punto implican nombres:

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    Los nombres implícitos de identificadores y expresiones de punto están disponibles a partir de Julia 1.5.


!!! compat "Julia 1.7"
    El uso de métodos `getindex` con múltiples `Symbol`s está disponible a partir de Julia 1.7.

