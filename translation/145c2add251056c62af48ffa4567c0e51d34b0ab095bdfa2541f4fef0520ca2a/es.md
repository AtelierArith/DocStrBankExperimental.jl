# [Arrays with custom indices](@id man-custom-indices)

Convencionalmente, los arreglos de Julia se indexan comenzando en 1, mientras que algunos otros lenguajes comienzan a numerar en 0, y otros (por ejemplo, Fortran) permiten especificar índices de inicio arbitrarios. Si bien hay mucho mérito en elegir un estándar (es decir, 1 para Julia), hay algunos algoritmos que se simplifican considerablemente si puedes indexar fuera del rango `1:size(A,d)` (y no solo `0:size(A,d)-1`, tampoco). Para facilitar tales cálculos, Julia admite arreglos con índices arbitrarios.

El propósito de esta página es abordar la pregunta: "¿qué tengo que hacer para soportar tales arreglos en mi propio código?" Primero, abordemos el caso más simple: si sabes que tu código nunca necesitará manejar arreglos con indexación no convencional, con suerte la respuesta es "nada". El código antiguo, en arreglos convencionales, debería funcionar esencialmente sin alteraciones siempre que estuviera utilizando las interfaces exportadas de Julia. Si te resulta más conveniente obligar a tus usuarios a proporcionar arreglos tradicionales donde la indexación comienza en uno, puedes agregar

```julia
Base.require_one_based_indexing(arrays...)
```

donde `arrays...` es una lista de los objetos de matriz que deseas verificar para cualquier cosa que viole la indexación basada en 1.

## Generalizing existing code

Como resumen, los pasos son:

  * Sure, please provide the Markdown content you'd like me to translate.
  * reemplazar `1:length(A)` con `eachindex(A)`, o en algunos casos `LinearIndices(A)`
  * reemplazar asignaciones explícitas como `Array{Int}(undef, size(B))` con `similar(Array{Int}, axes(B))`

Estos se describen con más detalle a continuación.

### Things to watch out for

Debido a que la indexación no convencional rompe muchas suposiciones de las personas de que todos los arreglos comienzan a indexarse desde 1, siempre existe la posibilidad de que el uso de tales arreglos desencadene errores. Los errores más frustrantes serían resultados incorrectos o segfaults (fallos totales de Julia). Por ejemplo, considera la siguiente función:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    length(dest) == length(src) || throw(DimensionMismatch("vectors must match"))
    # OK, now we're safe to use @inbounds, right? (not anymore!)
    for i = 1:length(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

Este código asume implícitamente que los vectores están indexados desde 1; si `dest` comienza en un índice diferente al de `src`, existe la posibilidad de que este código provoque un segfault. (Si obtienes segfaults, para ayudar a localizar la causa, intenta ejecutar julia con la opción `--check-bounds=yes`.)

### Using `axes` for bounds checks and loop iteration

`axes(A)` (rememorando `size(A)`) devuelve una tupla de objetos `AbstractUnitRange{<:Integer}`, especificando el rango de índices válidos a lo largo de cada dimensión de `A`. Cuando `A` tiene indexación no convencional, los rangos pueden no comenzar en 1. Si solo deseas el rango para una dimensión particular `d`, existe `axes(A, d)`.

Base implementa un tipo de rango personalizado, `OneTo`, donde `OneTo(n)` significa lo mismo que `1:n` pero en una forma que garantiza (a través del sistema de tipos) que el índice inferior es 1. Para cualquier nuevo tipo [`AbstractArray`](@ref), este es el valor predeterminado devuelto por `axes`, e indica que este tipo de arreglo utiliza indexación "convencional" basada en 1.

Para la verificación de límites, ten en cuenta que hay funciones dedicadas `checkbounds` y `checkindex` que a veces pueden simplificar tales pruebas.

### Linear indexing (`LinearIndices`)

Algunos algoritmos se escriben de manera más conveniente (o eficiente) en términos de un solo índice lineal, `A[i]`, incluso si `A` es multidimensional. Independientemente de los índices nativos del arreglo, los índices lineales siempre varían de `1:length(A)`. Sin embargo, esto plantea una ambigüedad para los arreglos unidimensionales (también conocidos como [`AbstractVector`](@ref)): ¿significa `v[i]` indexación lineal o indexación cartesiana con los índices nativos del arreglo?

Por esta razón, tu mejor opción puede ser iterar sobre el array con `eachindex(A)`, o, si necesitas que los índices sean enteros secuenciales, obtener el rango de índices llamando a `LinearIndices(A)`. Esto devolverá `axes(A, 1)` si A es un AbstractVector, y el equivalente de `1:length(A)` de lo contrario.

Por esta definición, los arreglos unidimensionales siempre utilizan indexación cartesiana con los índices nativos del arreglo. Para ayudar a hacer cumplir esto, vale la pena señalar que las funciones de conversión de índices generarán un error si la forma indica un arreglo unidimensional con indexación no convencional (es decir, es un `Tuple{UnitRange}` en lugar de un tuple de `OneTo`). Para los arreglos con indexación convencional, estas funciones continúan funcionando de la misma manera que siempre.

Usando `axes` y `LinearIndices`, aquí hay una forma en que podrías reescribir `mycopy!`:

```julia
function mycopy!(dest::AbstractVector, src::AbstractVector)
    axes(dest) == axes(src) || throw(DimensionMismatch("vectors must match"))
    for i in LinearIndices(src)
        @inbounds dest[i] = src[i]
    end
    dest
end
```

### Allocating storage using generalizations of `similar`

El almacenamiento a menudo se asigna con `Array{Int}(undef, dims)` o `similar(A, args...)`. Cuando el resultado necesita coincidir con los índices de otro array, esto puede no ser suficiente. El reemplazo genérico para tales patrones es usar `similar(storagetype, shape)`. `storagetype` indica el tipo de comportamiento "convencional" subyacente que te gustaría, por ejemplo, `Array{Int}` o `BitArray` o incluso `dims->zeros(Float32, dims)` (que asignaría un array de ceros). `shape` es una tupla de [`Integer`](@ref) o valores de `AbstractUnitRange`, especificando los índices que deseas que el resultado utilice. Ten en cuenta que una forma conveniente de producir un array de ceros que coincida con los índices de A es simplemente `zeros(A)`.

Vamos a repasar un par de ejemplos explícitos. Primero, si `A` tiene índices convencionales, entonces `similar(Array{Int}, axes(A))` terminaría llamando a `Array{Int}(undef, size(A))`, y por lo tanto devolvería un array. Si `A` es un tipo `AbstractArray` con indexación no convencional, entonces `similar(Array{Int}, axes(A))` debería devolver algo que "comporte como" un `Array{Int}` pero con una forma (incluyendo índices) que coincida con `A`. (La implementación más obvia es asignar un `Array{Int}(undef, size(A))` y luego "envolverlo" en un tipo que desplace los índices.)

Nota también que `similar(Array{Int}, (axes(A, 2),))` asignaría un `AbstractVector{Int}` (es decir, un arreglo unidimensional) que coincide con los índices de las columnas de `A`.

## Writing custom array types with non-1 indexing

La mayoría de los métodos que necesitarás definir son estándar para cualquier tipo de `AbstractArray`, consulta [Abstract Arrays](@ref man-interface-array). Esta página se centra en los pasos necesarios para definir indexación no convencional.

### Custom `AbstractUnitRange` types

Si estás escribiendo un tipo de arreglo que no está indexado en 1, querrás especializar `axes` para que devuelva un `UnitRange`, o (quizás mejor) un `AbstractUnitRange` personalizado. La ventaja de un tipo personalizado es que "señala" el tipo de asignación para funciones como `similar`. Si estamos escribiendo un tipo de arreglo para el cual la indexación comenzará en 0, probablemente queramos comenzar creando un nuevo `AbstractUnitRange`, `ZeroRange`, donde `ZeroRange(n)` es equivalente a `0:n-1`.

En general, probablemente *no* deberías exportar `ZeroRange` de tu paquete: puede haber otros paquetes que implementen su propio `ZeroRange`, y tener múltiples tipos distintos de `ZeroRange` es (quizás de manera contraintuitiva) una ventaja: `ModuleA.ZeroRange` indica que `similar` debería crear un `ModuleA.ZeroArray`, mientras que `ModuleB.ZeroRange` indica un tipo `ModuleB.ZeroArray`. Este diseño permite la coexistencia pacífica entre muchos tipos de arreglos personalizados diferentes.

Tenga en cuenta que el paquete de Julia [CustomUnitRanges.jl](https://github.com/JuliaArrays/CustomUnitRanges.jl) a veces se puede utilizar para evitar la necesidad de escribir su propio tipo `ZeroRange`.

### Specializing `axes`

Una vez que tengas tu tipo `AbstractUnitRange`, especializa `axes`:

```julia
Base.axes(A::ZeroArray) = map(n->ZeroRange(n), A.size)
```

donde aquí imaginamos que `ZeroArray` tiene un campo llamado `size` (habría otras formas de implementar esto).

En algunos casos, la definición de reserva para `axes(A, d)`:

```julia
axes(A::AbstractArray{T,N}, d) where {T,N} = d <= N ? axes(A)[d] : OneTo(1)
```

puede que no sea lo que deseas: es posible que necesites especializarlo para devolver algo diferente a `OneTo(1)` cuando `d > ndims(A)`. Del mismo modo, en `Base` hay una función dedicada `axes1` que es equivalente a `axes(A, 1)` pero que evita comprobar (en tiempo de ejecución) si `ndims(A) > 0`. (Esto es puramente una optimización de rendimiento.) Se define como:

```julia
axes1(A::AbstractArray{T,0}) where {T} = OneTo(1)
axes1(A::AbstractArray) = axes(A)[1]
```

Si el primero de estos (el caso de cero dimensiones) es problemático para tu tipo de arreglo personalizado, asegúrate de especializarlo adecuadamente.

### Specializing `similar`

Dado tu tipo personalizado `ZeroRange`, también deberías agregar las siguientes dos especializaciones para `similar`:

```julia
function Base.similar(A::AbstractArray, T::Type, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end

function Base.similar(f::Union{Function,DataType}, shape::Tuple{ZeroRange,Vararg{ZeroRange}})
    # body
end
```

Ambos de estos deberían asignar tu tipo de arreglo personalizado.

### Specializing `reshape`

Opcionalmente, define un método

```
Base.reshape(A::AbstractArray, shape::Tuple{ZeroRange,Vararg{ZeroRange}}) = ...
```

y también puedes `reshape` un array de modo que el resultado tenga índices personalizados.

### For objects that mimic AbstractArray but are not subtypes

`has_offset_axes` depende de tener `axes` definidos para los objetos sobre los que lo llamas. Si hay alguna razón por la que no tienes un método `axes` definido para tu objeto, considera definir un método.

```julia
Base.has_offset_axes(obj::MyNon1IndexedArraylikeObject) = true
```

Esto permitirá que el código que asume un índice basado en 1 detecte un problema y arroje un error útil, en lugar de devolver resultados incorrectos o provocar un fallo de segmentación en Julia.

### Catching errors

Si tu nuevo tipo de arreglo provoca errores en otro código, un paso útil para depurar puede ser comentar `@boundscheck` en tu implementación de `getindex` y `setindex!`. Esto asegurará que cada acceso a un elemento verifique los límites. O, reinicia julia con `--check-bounds=yes`.

En algunos casos, también puede ser útil deshabilitar temporalmente `size` y `length` para su nuevo tipo de arreglo, ya que el código que hace suposiciones incorrectas utiliza con frecuencia estas funciones.
