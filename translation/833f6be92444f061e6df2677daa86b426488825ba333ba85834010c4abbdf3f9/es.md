# Bounds checking

Como muchos lenguajes de programación modernos, Julia utiliza la verificación de límites para garantizar la seguridad del programa al acceder a arreglos. En bucles internos ajustados u otras situaciones críticas de rendimiento, es posible que desee omitir estas verificaciones de límites para mejorar el rendimiento en tiempo de ejecución. Por ejemplo, para emitir instrucciones vectorizadas (SIMD), el cuerpo de su bucle no puede contener ramas y, por lo tanto, no puede contener verificaciones de límites. En consecuencia, Julia incluye un macro `@inbounds(...)` para indicar al compilador que omita tales verificaciones de límites dentro del bloque dado. Los tipos de arreglos definidos por el usuario pueden utilizar el macro `@boundscheck(...)` para lograr una selección de código sensible al contexto.

## Eliding bounds checks

El `@boundscheck(...)` macro marca bloques de código que realizan verificación de límites. Cuando tales bloques se insertan en un bloque `@inbounds(...)`, el compilador puede eliminar estos bloques. El compilador elimina el bloque `@boundscheck` *solo si está insertado* en la función que lo llama. Por ejemplo, podrías escribir el método `sum` como:

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

Con un tipo personalizado similar a un array `MyArray` que tiene:

```julia
@inline getindex(A::MyArray, i::Real) = (@boundscheck checkbounds(A, i); A.data[to_index(i)])
```

Entonces, cuando `getindex` se inserta en `sum`, la llamada a `checkbounds(A, i)` será eliminada. Si tu función contiene múltiples capas de inserción, solo los bloques `@boundscheck` a lo sumo un nivel de inserción más profundo son eliminados. La regla previene cambios no intencionados en el comportamiento del programa debido a código más arriba en la pila.

### Caution!

Es fácil exponer accidentalmente operaciones inseguras con `@inbounds`. Podrías sentirte tentado a escribir el ejemplo anterior como

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in 1:length(A)
        @inbounds r += A[i]
    end
    return r
end
```

Lo que asume silenciosamente la indexación basada en 1 y, por lo tanto, expone el acceso inseguro a la memoria cuando se usa con [`OffsetArrays`](@ref man-custom-indices):

```julia-repl
julia> using OffsetArrays

julia> sum(OffsetArray([1, 2, 3], -10))
9164911648 # inconsistent results or segfault
```

Mientras que la fuente original del error aquí es `1:length(A)`, el uso de `@inbounds` aumenta las consecuencias de un error de límites a un acceso a memoria inseguro que es menos fácilmente detectado y depurado. A menudo es difícil o imposible probar que un método que utiliza `@inbounds` es seguro, por lo que se deben sopesar los beneficios de las mejoras de rendimiento contra el riesgo de fallos de segmentación y comportamientos silenciosos incorrectos, especialmente en APIs de cara al público.

## Propagating inbounds

Puede haber ciertos escenarios en los que, por razones de organización del código, desees más de una capa entre las declaraciones `@inbounds` y `@boundscheck`. Por ejemplo, los métodos predeterminados `getindex` tienen la cadena `getindex(A::AbstractArray, i::Real)` llama a `getindex(IndexStyle(A), A, i)` llama a `_getindex(::IndexLinear, A, i)`.

Para anular la regla de "una capa de inlining", una función puede ser marcada con [`Base.@propagate_inbounds`](@ref) para propagar un contexto inbounds (o un contexto out of bounds) a través de una capa adicional de inlining.

## The bounds checking call hierarchy

La jerarquía general es:

  * `checkbounds(A, I...)` que llama a

      * `checkbounds(Bool, A, I...)` que llama a

          * `checkbounds_indices(Bool, axes(A), I)` que llama recursivamente

              * `checkindex` para cada dimensión

Aquí `A` es el arreglo, y `I` contiene los índices "solicitados". `axes(A)` devuelve una tupla de índices "permitidos" de `A`.

`checkbounds(A, I...)` lanza un error si los índices son inválidos, mientras que `checkbounds(Bool, A, I...)` devuelve `false` en esa circunstancia. `checkbounds_indices` descarta cualquier información sobre el arreglo además de su tupla de `axes`, y realiza una comparación pura de índices contra índices: esto permite que relativamente pocos métodos compilados sirvan a una gran variedad de tipos de arreglos. Los índices se especifican como tuplas, y generalmente se comparan de manera 1-1 con dimensiones individuales manejadas al llamar a otra función importante, `checkindex`: típicamente,

```julia
checkbounds_indices(Bool, (IA1, IA...), (I1, I...)) = checkindex(Bool, IA1, I1) &
                                                      checkbounds_indices(Bool, IA, I)
```

así `checkindex` verifica una sola dimensión. Todas estas funciones, incluida la no exportada `checkbounds_indices`, tienen cadenas de documentación accesibles con `?`.

Si tienes que personalizar la verificación de límites para un tipo de arreglo específico, deberías especializar `checkbounds(Bool, A, I...)`. Sin embargo, en la mayoría de los casos deberías poder confiar en `checkbounds_indices` siempre que proporciones `axes` útiles para tu tipo de arreglo.

Si tienes tipos de índice novedosos, primero considera especializar `checkindex`, que maneja un solo índice para una dimensión particular de un arreglo. Si tienes un tipo de índice multidimensional personalizado (similar a `CartesianIndex`), entonces puede que tengas que considerar especializar `checkbounds_indices`.

Tenga en cuenta que esta jerarquía ha sido diseñada para reducir la probabilidad de ambigüedades en los métodos. Intentamos hacer de `checkbounds` el lugar para especializarse en el tipo de arreglo, y tratamos de evitar especializaciones en los tipos de índice; por el contrario, `checkindex` está destinado a especializarse solo en el tipo de índice (especialmente, el último argumento).

## Emit bounds checks

Julia se puede iniciar con `--check-bounds={yes|no|auto}` para emitir comprobaciones de límites siempre, nunca, o respetar las declaraciones `@inbounds`.
