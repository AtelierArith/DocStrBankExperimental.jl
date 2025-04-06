# [Missing Values](@id missing)

Julia proporciona soporte para representar valores faltantes en el sentido estadístico. Esto es para situaciones en las que no hay un valor disponible para una variable en una observación, pero teóricamente existe un valor válido. Los valores faltantes se representan a través del objeto [`missing`](@ref), que es la instancia singleton del tipo [`Missing`](@ref). `missing` es equivalente a [`NULL` in SQL](https://en.wikipedia.org/wiki/NULL_(SQL)) y [`NA` in R](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#NA-handling), y se comporta como ellos en la mayoría de las situaciones.

## Propagation of Missing Values

Los valores `missing` *se propagan* automáticamente cuando se pasan a operadores y funciones matemáticas estándar. Para estas funciones, la incertidumbre sobre el valor de uno de los operandos induce incertidumbre sobre el resultado. En la práctica, esto significa que una operación matemática que involucra un valor `missing` generalmente devuelve `missing`:

```jldoctest
julia> missing + 1
missing

julia> "a" * missing
missing

julia> abs(missing)
missing
```

Dado que `missing` es un objeto normal de Julia, esta regla de propagación solo funciona para funciones que han optado por implementar este comportamiento. Esto se puede lograr mediante:

  * agregando un método específico definido para argumentos de tipo `Missing`,
  * aceptando argumentos de este tipo y pasándolos a funciones que los propagan (como los operadores matemáticos estándar).

Los paquetes deben considerar si tiene sentido propagar valores faltantes al definir nuevas funciones y definir los métodos apropiadamente si este es el caso. Pasar un valor `missing` a una función que no tiene un método que acepte argumentos del tipo `Missing` genera un [`MethodError`](@ref), al igual que para cualquier otro tipo.

Las funciones que no propagan valores `missing` pueden hacerse para que lo hagan envolviéndolas en la función `passmissing` proporcionada por el paquete [Missings.jl](https://github.com/JuliaData/Missings.jl). Por ejemplo, `f(x)` se convierte en `passmissing(f)(x)`.

## Equality and Comparison Operators

Los operadores de igualdad y comparación estándar siguen la regla de propagación presentada anteriormente: si alguno de los operandos está `faltante`, el resultado es `faltante`. Aquí hay algunos ejemplos:

```jldoctest
julia> missing == 1
missing

julia> missing == missing
missing

julia> missing < 1
missing

julia> 2 >= missing
missing
```

En particular, ten en cuenta que `missing == missing` devuelve `missing`, por lo que `==` no se puede usar para probar si un valor está ausente. Para probar si `x` está `missing`, utiliza [`ismissing(x)`](@ref).

Los operadores de comparación especiales [`isequal`](@ref) y [`===`](@ref) son excepciones a la regla de propagación. Siempre devolverán un valor `Bool`, incluso en presencia de valores `missing`, considerando `missing` como igual a `missing` y diferente de cualquier otro valor. Por lo tanto, se pueden utilizar para probar si un valor es `missing`:

```jldoctest
julia> missing === 1
false

julia> isequal(missing, 1)
false

julia> missing === missing
true

julia> isequal(missing, missing)
true
```

El operador [`isless`](@ref) es otra excepción: `missing` se considera mayor que cualquier otro valor. Este operador es utilizado por [`sort!`](@ref), que por lo tanto coloca los valores `missing` después de todos los demás valores:

```jldoctest
julia> isless(1, missing)
true

julia> isless(missing, Inf)
false

julia> isless(missing, missing)
false
```

## Logical operators

Los operadores lógicos (o booleanos) [`|`](@ref), [`&`](@ref) y [`xor`](@ref) son otro caso especial ya que solo propagan valores `missing` cuando es lógicamente necesario. Para estos operadores, si el resultado es incierto o no, depende de la operación particular. Esto sigue las reglas bien establecidas de [*three-valued logic*](https://en.wikipedia.org/wiki/Three-valued_logic), que están implementadas por ejemplo en `NULL` en SQL y `NA` en R. Esta definición abstracta corresponde a un comportamiento relativamente natural que se explica mejor a través de ejemplos concretos.

Ilustremos este principio con el operador lógico "o" [`|`](@ref). Siguiendo las reglas de la lógica booleana, si uno de los operandos es `true`, el valor del otro operando no tiene influencia en el resultado, que siempre será `true`:

```jldoctest
julia> true | true
true

julia> true | false
true

julia> false | true
true
```

Basado en esta observación, podemos concluir que si uno de los operandos es `true` y el otro es `missing`, sabemos que el resultado es `true` a pesar de la incertidumbre sobre el valor real de uno de los operandos. Si hubiéramos podido observar el valor real del segundo operando, solo podría ser `true` o `false`, y en ambos casos el resultado sería `true`. Por lo tanto, en este caso particular, la falta de datos *no* se propaga:

```jldoctest
julia> true | missing
true

julia> missing | true
true
```

Por el contrario, si uno de los operandos es `false`, el resultado podría ser `true` o `false` dependiendo del valor del otro operando. Por lo tanto, si ese operando está `missing`, el resultado también tiene que ser `missing`:

```jldoctest
julia> false | true
true

julia> true | false
true

julia> false | false
false

julia> false | missing
missing

julia> missing | false
missing
```

El comportamiento del operador lógico "y" [`&`](@ref) es similar al del operador `|`, con la diferencia de que la falta de datos no se propaga cuando uno de los operandos es `false`. Por ejemplo, cuando ese es el caso del primer operando:

```jldoctest
julia> false & false
false

julia> false & true
false

julia> false & missing
false
```

Por otro lado, la falta de datos se propaga cuando uno de los operandos es `true`, por ejemplo, el primero:

```jldoctest
julia> true & true
true

julia> true & false
false

julia> true & missing
missing
```

Finalmente, el operador lógico "o exclusivo" [`xor`](@ref) siempre propaga valores `missing`, ya que ambos operandos siempre tienen un efecto en el resultado. También ten en cuenta que el operador de negación [`!`](@ref) devuelve `missing` cuando el operando es `missing`, al igual que otros operadores unarios.

## Control Flow and Short-Circuiting Operators

Los operadores de control de flujo, incluyendo [`if`](@ref), [`while`](@ref) y el [ternary operator](@ref man-conditional-evaluation) `x ? y : z`, no permiten valores faltantes. Esto se debe a la incertidumbre sobre si el valor real sería `true` o `false` si pudiéramos observarlo. Esto implica que no sabemos cómo debería comportarse el programa. En este caso, se lanza un [`TypeError`](@ref) tan pronto como se encuentra un valor `missing` en este contexto:

```jldoctest
julia> if missing
           println("here")
       end
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

Por la misma razón, a diferencia de los operadores lógicos presentados anteriormente, los operadores booleanos de cortocircuito [`&&`](@ref) y [`||`](@ref) no permiten valores `missing` en situaciones donde el valor del operando determina si el siguiente operando se evalúa o no. Por ejemplo:

```jldoctest
julia> missing || false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context

julia> true && missing && false
ERROR: TypeError: non-boolean (Missing) used in boolean context
```

En contraste, no se lanza ningún error cuando el resultado se puede determinar sin los valores `missing`. Este es el caso cuando el código se interrumpe antes de evaluar el operando `missing`, y cuando el operando `missing` es el último:

```jldoctest
julia> true && missing
missing

julia> false && missing
false
```

## Arrays With Missing Values

Los arreglos que contienen valores faltantes se pueden crear como otros arreglos:

```jldoctest
julia> [1, missing]
2-element Vector{Union{Missing, Int64}}:
 1
  missing
```

Como muestra este ejemplo, el tipo de elemento de tales arreglos es `Union{Missing, T}`, siendo `T` el tipo de los valores no faltantes. Esto refleja el hecho de que las entradas del arreglo pueden ser de tipo `T` (aquí, `Int64`) o de tipo `Missing`. Este tipo de arreglo utiliza un almacenamiento de memoria eficiente equivalente a un `Array{T}` que contiene los valores reales combinado con un `Array{UInt8}` que indica el tipo de la entrada (es decir, si es `Missing` o `T`).

Los arreglos que permiten valores faltantes se pueden construir con la sintaxis estándar. Usa `Array{Union{Missing, T}}(missing, dims)` para crear arreglos llenos de valores faltantes:

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```

!!! note
    Usar `undef` o `similar` puede actualmente dar un array lleno de `missing`, pero esta no es la forma correcta de obtener tal array. Usa un constructor de `missing` como se mostró arriba en su lugar.


Un arreglo con un tipo de elemento que permite entradas `missing` (por ejemplo, `Vector{Union{Missing, T}}`) que no contiene ninguna entrada `missing` se puede convertir a un tipo de arreglo que no permite entradas `missing` (por ejemplo, `Vector{T}`) utilizando [`convert`](@ref). Si el arreglo contiene valores `missing`, se lanza un `MethodError` durante la conversión:

```jldoctest
julia> x = Union{Missing, String}["a", "b"]
2-element Vector{Union{Missing, String}}:
 "a"
 "b"

julia> convert(Array{String}, x)
2-element Vector{String}:
 "a"
 "b"

julia> y = Union{Missing, String}[missing, "b"]
2-element Vector{Union{Missing, String}}:
 missing
 "b"

julia> convert(Array{String}, y)
ERROR: MethodError: Cannot `convert` an object of type Missing to an object of type String
```

## Skipping Missing Values

Dado que los valores `missing` se propagan con los operadores matemáticos estándar, las funciones de reducción devuelven `missing` cuando se llaman en arreglos que contienen valores faltantes:

```jldoctest
julia> sum([1, missing])
missing
```

En esta situación, utiliza la función [`skipmissing`](@ref) para omitir valores faltantes:

```jldoctest
julia> sum(skipmissing([1, missing]))
1
```

Esta función de conveniencia devuelve un iterador que filtra eficientemente los valores `missing`. Por lo tanto, se puede utilizar con cualquier función que soporte iteradores:

```jldoctest skipmissing
julia> x = skipmissing([3, missing, 2, 1])
skipmissing(Union{Missing, Int64}[3, missing, 2, 1])

julia> maximum(x)
3

julia> sum(x)
6

julia> mapreduce(sqrt, +, x)
4.146264369941973
```

Los objetos creados al llamar a `skipmissing` en un arreglo se pueden indexar utilizando índices del arreglo padre. Los índices que corresponden a valores faltantes no son válidos para estos objetos, y se lanza un error al intentar usarlos (también se omiten en `keys` y `eachindex`):

```jldoctest skipmissing
julia> x[1]
3

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]
```

Esto permite que las funciones que operan sobre índices funcionen en combinación con `skipmissing`. Este es el caso notable de las funciones de búsqueda y localización. Estas funciones devuelven índices válidos para el objeto devuelto por `skipmissing`, y también son los índices de las entradas coincidentes *en el array padre*:

```jldoctest skipmissing
julia> findall(==(1), x)
1-element Vector{Int64}:
 4

julia> findfirst(!iszero, x)
1

julia> argmax(x)
1
```

Utiliza [`collect`](@ref) para extraer valores no `faltantes` y almacenarlos en un arreglo:

```jldoctest skipmissing
julia> collect(x)
3-element Vector{Int64}:
 3
 2
 1
```

## Logical Operations on Arrays

La lógica de tres valores descrita anteriormente para los operadores lógicos también se utiliza en funciones lógicas aplicadas a arreglos. Así, las pruebas de igualdad de arreglos utilizando el operador [`==`](@ref) devuelven `missing` siempre que el resultado no se pueda determinar sin conocer el valor real de la entrada `missing`. En la práctica, esto significa que se devuelve `missing` si todos los valores no faltantes de los arreglos comparados son iguales, pero uno o ambos arreglos contienen valores faltantes (posiblemente en diferentes posiciones):

```jldoctest
julia> [1, missing] == [2, missing]
false

julia> [1, missing] == [1, missing]
missing

julia> [1, 2, missing] == [1, missing, 2]
missing
```

En cuanto a los valores individuales, utiliza [`isequal`](@ref) para tratar los valores `missing` como iguales a otros valores `missing`, pero diferentes de los valores no `missing`:

```jldoctest
julia> isequal([1, missing], [1, missing])
true

julia> isequal([1, 2, missing], [1, missing, 2])
false
```

Las funciones [`any`](@ref) y [`all`](@ref) también siguen las reglas de la lógica de tres valores. Por lo tanto, devuelven `missing` cuando el resultado no puede ser determinado:

```jldoctest
julia> all([true, missing])
missing

julia> all([false, missing])
false

julia> any([true, missing])
true

julia> any([false, missing])
missing
```
