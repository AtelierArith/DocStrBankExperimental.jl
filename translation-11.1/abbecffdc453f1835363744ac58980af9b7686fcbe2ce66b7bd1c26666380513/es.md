# Interfaces

Gran parte del poder y la extensibilidad en Julia proviene de una colección de interfaces informales. Al extender algunos métodos específicos para que funcionen con un tipo personalizado, los objetos de ese tipo no solo reciben esas funcionalidades, sino que también pueden ser utilizados en otros métodos que están escritos para construir genéricamente sobre esos comportamientos.

## [Iteration](@id man-interface-iteration)

Hay dos métodos que siempre son necesarios:

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

Hay varios métodos más que deben definirse en algunas circunstancias. Tenga en cuenta que siempre debe definir al menos uno de `Base.IteratorSize(IterType)` y `length(iter)` porque la definición predeterminada de `Base.IteratorSize(IterType)` es `Base.HasLength()`.

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

La iteración secuencial se implementa mediante la función [`iterate`](@ref). En lugar de mutar objetos mientras se iteran, los iteradores de Julia pueden llevar un seguimiento del estado de la iteración externamente al objeto. El valor de retorno de `iterate` es siempre una tupla de un valor y un estado, o `nothing` si no quedan elementos. El objeto de estado se pasará de vuelta a la función `iterate` en la siguiente iteración y generalmente se considera un detalle de implementación privado al objeto iterable.

Cualquier objeto que defina esta función es iterable y se puede usar en el [many functions that rely upon iteration](@ref lib-collections-iteration). También se puede usar directamente en un bucle [`for`](@ref) ya que la sintaxis:

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

es se traduce en:

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

Un ejemplo simple es una secuencia iterable de números cuadrados con una longitud definida:

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

Con solo [`iterate`](@ref) definición, el tipo `Squares` ya es bastante poderoso. Podemos iterar sobre todos los elementos:

```jldoctest squaretype
julia> for item in Squares(7)
           println(item)
       end
1
4
9
16
25
36
49
```

Podemos usar muchos de los métodos integrados que funcionan con iterables, como [`in`](@ref) o [`sum`](@ref):

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

Hay algunos métodos más que podemos extender para darle a Julia más información sobre esta colección iterable. Sabemos que los elementos en una secuencia de `Squares` siempre serán `Int`. Al extender el método [`eltype`](@ref), podemos darle esa información a Julia y ayudarle a generar código más especializado en los métodos más complicados. También sabemos el número de elementos en nuestra secuencia, así que podemos extender [`length`](@ref), también:

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

Ahora, cuando le pedimos a Julia que [`collect`](@ref) todos los elementos en un array, puede preasignar un `Vector{Int}` del tamaño correcto en lugar de ingenuamente [`push!`](@ref) cada elemento en un `Vector{Any}`:

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

Mientras podemos confiar en implementaciones genéricas, también podemos extender métodos específicos donde sabemos que hay un algoritmo más simple. Por ejemplo, hay una fórmula para calcular la suma de cuadrados, por lo que podemos anular la versión iterativa genérica con una solución más eficiente:

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

Este es un patrón muy común en Julia Base: un pequeño conjunto de métodos requeridos define una interfaz informal que permite muchos comportamientos más sofisticados. En algunos casos, los tipos querrán especializar adicionalmente esos comportamientos extra cuando saben que se puede utilizar un algoritmo más eficiente en su caso específico.

También suele ser útil permitir la iteración sobre una colección en *orden inverso* iterando sobre [`Iterators.reverse(iterator)`](@ref). Sin embargo, para admitir realmente la iteración en orden inverso, un tipo de iterador `T` necesita implementar `iterate` para `Iterators.Reverse{T}`. (Dado `r::Iterators.Reverse{T}`, el iterador subyacente de tipo `T` es `r.itr`.) En nuestro ejemplo de `Squares`, implementaríamos los métodos de `Iterators.Reverse{Squares}`:

```jldoctest squaretype
julia> Base.iterate(rS::Iterators.Reverse{Squares}, state=rS.itr.count) = state < 1 ? nothing : (state*state, state-1)

julia> collect(Iterators.reverse(Squares(4)))
4-element Vector{Int64}:
 16
  9
  4
  1
```

## Indexing

| Methods to implement | Brief description                                             |
|:-------------------- |:------------------------------------------------------------- |
| `getindex(X, i)`     | `X[i]`, indexed access, non-scalar `i` should allocate a copy |
| `setindex!(X, v, i)` | `X[i] = v`, indexed assignment                                |
| `firstindex(X)`      | The first index, used in `X[begin]`                           |
| `lastindex(X)`       | The last index, used in `X[end]`                              |

Para el iterable `Squares` mencionado anteriormente, podemos calcular fácilmente el `i`-ésimo elemento de la secuencia al elevarlo al cuadrado. Podemos exponer esto como una expresión de indexación `S[i]`. Para optar por este comportamiento, `Squares` simplemente necesita definir [`getindex`](@ref):

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

Además, para soportar la sintaxis `S[begin]` y `S[end]`, debemos definir [`firstindex`](@ref) y [`lastindex`](@ref) para especificar los primeros y últimos índices válidos, respectivamente:

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

Para la indexación multi-dimensional `begin`/`end` como en `a[3, begin, 7]`, por ejemplo, debes definir `firstindex(a, dim)` y `lastindex(a, dim)` (que por defecto llaman a `first` y `last` en `axes(a, dim)`, respectivamente).

Nota, sin embargo, que lo anterior *solo* define [`getindex`](@ref) con un índice entero. Indexar con cualquier cosa que no sea un `Int` lanzará un [`MethodError`](@ref) diciendo que no había un método coincidente. Para soportar la indexación con rangos o vectores de `Int`s, deben escribirse métodos separados:

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

Mientras esto comienza a soportar más de las [indexing operations supported by some of the builtin types](@ref man-array-indexing), todavía hay un buen número de comportamientos que faltan. Esta secuencia de `Squares` comienza a parecerse más y más a un vector a medida que hemos añadido comportamientos a ella. En lugar de definir todos estos comportamientos nosotros mismos, podemos definirlo oficialmente como un subtipo de un [`AbstractArray`](@ref).

## [Abstract Arrays](@id man-interface-array)

| Methods to implement                     |                                        | Brief description                                                                                                                                                |
|:---------------------------------------- |:-------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `size(A)`                                |                                        | Returns a tuple containing the dimensions of `A`                                                                                                                 |
| `getindex(A, i::Int)`                    |                                        | (if `IndexLinear`) Linear scalar indexing                                                                                                                        |
| `getindex(A, I::Vararg{Int, N})`         |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexing                                                                                        |
| **Optional methods**                     | **Default definition**                 | **Brief description**                                                                                                                                            |
| `IndexStyle(::Type)`                     | `IndexCartesian()`                     | Returns either `IndexLinear()` or `IndexCartesian()`. See the description below.                                                                                 |
| `setindex!(A, v, i::Int)`                |                                        | (if `IndexLinear`) Scalar indexed assignment                                                                                                                     |
| `setindex!(A, v, I::Vararg{Int, N})`     |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexed assignment                                                                              |
| `getindex(A, I...)`                      | defined in terms of scalar `getindex`  | [Multidimensional and nonscalar indexing](@ref man-array-indexing)                                                                                               |
| `setindex!(A, X, I...)`                  | defined in terms of scalar `setindex!` | [Multidimensional and nonscalar indexed assignment](@ref man-array-indexing)                                                                                     |
| `iterate`                                | defined in terms of scalar `getindex`  | Iteration                                                                                                                                                        |
| `length(A)`                              | `prod(size(A))`                        | Number of elements                                                                                                                                               |
| `similar(A)`                             | `similar(A, eltype(A), size(A))`       | Return a mutable array with the same shape and element type                                                                                                      |
| `similar(A, ::Type{S})`                  | `similar(A, S, size(A))`               | Return a mutable array with the same shape and the specified element type                                                                                        |
| `similar(A, dims::Dims)`                 | `similar(A, eltype(A), dims)`          | Return a mutable array with the same element type and size *dims*                                                                                                |
| `similar(A, ::Type{S}, dims::Dims)`      | `Array{S}(undef, dims)`                | Return a mutable array with the specified element type and size                                                                                                  |
| **Non-traditional indices**              | **Default definition**                 | **Brief description**                                                                                                                                            |
| `axes(A)`                                | `map(OneTo, size(A))`                  | Return a tuple of `AbstractUnitRange{<:Integer}` of valid indices. The axes should be their own axes, that is `axes.(axes(A),1) == axes(A)` should be satisfied. |
| `similar(A, ::Type{S}, inds)`            | `similar(A, S, Base.to_shape(inds))`   | Return a mutable array with the specified indices `inds` (see below)                                                                                             |
| `similar(T::Union{Type,Function}, inds)` | `T(Base.to_shape(inds))`               | Return an array similar to `T` with the specified indices `inds` (see below)                                                                                     |

Si un tipo se define como un subtipo de `AbstractArray`, hereda un conjunto muy grande de comportamientos ricos, incluyendo la iteración y la indexación multidimensional construida sobre el acceso a un solo elemento. Consulta el [arrays manual page](@ref man-multi-dim-arrays) y el [Julia Base section](@ref lib-arrays) para más métodos soportados.

Una parte clave en la definición de un subtipo de `AbstractArray` es [`IndexStyle`](@ref). Dado que la indexación es una parte tan importante de un array y a menudo ocurre en bucles críticos, es importante hacer que tanto la indexación como la asignación indexada sean lo más eficientes posible. Las estructuras de datos de array se definen típicamente de una de dos maneras: o accede a sus elementos de la manera más eficiente utilizando solo un índice (indexación lineal) o accede intrínsecamente a los elementos con índices especificados para cada dimensión. Estas dos modalidades son identificadas por Julia como `IndexLinear()` y `IndexCartesian()`. Convertir un índice lineal a múltiples subíndices de indexación suele ser muy costoso, por lo que esto proporciona un mecanismo basado en rasgos para habilitar código genérico eficiente para todos los tipos de array.

Esta distinción determina qué métodos de indexación escalar debe definir el tipo. Los arreglos `IndexLinear()` son simples: solo se define `getindex(A::ArrayType, i::Int)`. Cuando el arreglo se indexa posteriormente con un conjunto multidimensional de índices, el método de respaldo `getindex(A::AbstractArray, I...)` convierte eficientemente los índices en un índice lineal y luego llama al método anterior. Los arreglos `IndexCartesian()`, por otro lado, requieren que se definan métodos para cada dimensionalidad soportada con índices `Int` de `ndims(A)`. Por ejemplo, [`SparseMatrixCSC`](@ref) del módulo de la biblioteca estándar `SparseArrays`, solo soporta dos dimensiones, por lo que solo define `getindex(A::SparseMatrixCSC, i::Int, j::Int)`. Lo mismo ocurre con [`setindex!`](@ref).

Regresando a la secuencia de cuadrados de arriba, podríamos definirla en su lugar como un subtipo de un `AbstractArray{Int, 1}`:

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

Tenga en cuenta que es muy importante especificar los dos parámetros de la `AbstractArray`; el primero define el [`eltype`](@ref), y el segundo define el [`ndims`](@ref). Ese supertipo y esos tres métodos son todo lo que se necesita para que `SquaresVector` sea un array iterable, indexable y completamente funcional:

```jldoctest squarevectype
julia> s = SquaresVector(4)
4-element SquaresVector:
  1
  4
  9
 16

julia> s[s .> 8]
2-element Vector{Int64}:
  9
 16

julia> s + s
4-element Vector{Int64}:
  2
  8
 18
 32

julia> sin.(s)
4-element Vector{Float64}:
  0.8414709848078965
 -0.7568024953079282
  0.4121184852417566
 -0.2879033166650653
```

Como un ejemplo más complicado, definamos nuestro propio tipo de arreglo disperso-like N-dimensional construido sobre [`Dict`](@ref):

```jldoctest squarevectype
julia> struct SparseArray{T,N} <: AbstractArray{T,N}
           data::Dict{NTuple{N,Int}, T}
           dims::NTuple{N,Int}
       end

julia> SparseArray(::Type{T}, dims::Int...) where {T} = SparseArray(T, dims);

julia> SparseArray(::Type{T}, dims::NTuple{N,Int}) where {T,N} = SparseArray{T,N}(Dict{NTuple{N,Int}, T}(), dims);

julia> Base.size(A::SparseArray) = A.dims

julia> Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where {T} = SparseArray(T, dims)

julia> Base.getindex(A::SparseArray{T,N}, I::Vararg{Int,N}) where {T,N} = get(A.data, I, zero(T))

julia> Base.setindex!(A::SparseArray{T,N}, v, I::Vararg{Int,N}) where {T,N} = (A.data[I] = v)
```

Tenga en cuenta que este es un `IndexCartesian` array, por lo que debemos definir manualmente [`getindex`](@ref) y [`setindex!`](@ref) en la dimensionalidad del array. A diferencia del `SquaresVector`, podemos definir `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566`, y así podemos mutar el array:

```jldoctest squarevectype
julia> A = SparseArray(Float64, 3, 3)
3×3 SparseArray{Float64, 2}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2)
3×3 SparseArray{Float64, 2}:
 2.0  2.0  2.0
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> A[:] = 1:length(A); A
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

El resultado de indexar un `AbstractArray` puede ser a su vez un array (por ejemplo, al indexar por un `AbstractRange`). Los métodos de retroceso de `AbstractArray` utilizan [`similar`](@ref) para asignar un `Array` del tamaño y tipo de elemento apropiados, que se llena utilizando el método de indexación básica descrito anteriormente. Sin embargo, al implementar un envoltorio de array, a menudo deseas que el resultado también esté envuelto:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

En este ejemplo se logra definiendo `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) donde T` para crear el arreglo envuelto apropiado. (Nota que aunque `similar` soporta formas de 1 y 2 argumentos, en la mayoría de los casos solo necesitas especializar la forma de 3 argumentos). Para que esto funcione es importante que `SparseArray` sea mutable (soporte `setindex!`). Definir `similar`, `getindex` y `setindex!` para `SparseArray` también hace posible [`copy`](@ref) el arreglo:

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

Además de todos los métodos iterables e indexables mencionados anteriormente, estos tipos también pueden interactuar entre sí y utilizar la mayoría de los métodos definidos en Julia Base para `AbstractArrays`:

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

Si estás definiendo un tipo de arreglo que permite indexación no tradicional (índices que comienzan en algo diferente a 1), deberías especializar [`axes`](@ref). También deberías especializar [`similar`](@ref) para que el argumento `dims` (normalmente una tupla de tamaño `Dims`) pueda aceptar objetos `AbstractUnitRange`, quizás tipos de rango `Ind` de tu propio diseño. Para más información, consulta [Arrays with custom indices](@ref man-custom-indices).

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

Un array estratificado es un subtipo de `AbstractArray` cuyas entradas se almacenan en memoria con pasos fijos. Siempre que el tipo de elemento del array sea compatible con BLAS, un array estratificado puede utilizar rutinas de BLAS y LAPACK para realizar rutinas de álgebra lineal de manera más eficiente. Un ejemplo típico de un array estratificado definido por el usuario es uno que envuelve un `Array` estándar con una estructura adicional.

Advertencia: no implemente estos métodos si el almacenamiento subyacente no es realmente estratificado, ya que puede llevar a resultados incorrectos o fallos de segmentación.

Aquí hay algunos ejemplos para demostrar qué tipo de arreglos son estratificados y cuáles no:

```julia
1:5   # not strided (there is no storage associated with this array.)
Vector(1:5)  # is strided with strides (1,)
A = [1 5; 2 6; 3 7; 4 8]  # is strided with strides (1,4)
V = view(A, 1:2, :)   # is strided with strides (1,4)
V = view(A, 1:2:3, 1:2)   # is strided with strides (2,4)
V = view(A, [1,2,4], :)   # is not strided, as the spacing between rows is not fixed.
```

## [Customizing broadcasting](@id man-interfaces-broadcasting)

| Methods to implement                                       | Brief description                                                  |
|:---------------------------------------------------------- |:------------------------------------------------------------------ |
| `Base.BroadcastStyle(::Type{SrcType}) = SrcStyle()`        | Broadcasting behavior of `SrcType`                                 |
| `Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})` | Allocation of output container                                     |
| **Optional methods**                                       |                                                                    |
| `Base.BroadcastStyle(::Style1, ::Style2) = Style12()`      | Precedence rules for mixing styles                                 |
| `Base.axes(x)`                                             | Declaration of the indices of `x`, as per [`axes(x)`](@ref).       |
| `Base.broadcastable(x)`                                    | Convert `x` to an object that has `axes` and supports indexing     |
| **Bypassing default machinery**                            |                                                                    |
| `Base.copy(bc::Broadcasted{DestStyle})`                    | Custom implementation of `broadcast`                               |
| `Base.copyto!(dest, bc::Broadcasted{DestStyle})`           | Custom implementation of `broadcast!`, specializing on `DestStyle` |
| `Base.copyto!(dest::DestType, bc::Broadcasted{Nothing})`   | Custom implementation of `broadcast!`, specializing on `DestType`  |
| `Base.Broadcast.broadcasted(f, args...)`                   | Override the default lazy behavior within a fused expression       |
| `Base.Broadcast.instantiate(bc::Broadcasted{DestStyle})`   | Override the computation of the lazy broadcast's axes              |

[Broadcasting](@ref) se activa mediante una llamada explícita a `broadcast` o `broadcast!`, o implícitamente mediante operaciones de "punto" como `A .+ b` o `f.(x, y)`. Cualquier objeto que tenga [`axes`](@ref) y que soporte indexación puede participar como argumento en la transmisión, y por defecto el resultado se almacena en un `Array`. Este marco básico es extensible de tres maneras principales:

  * Asegurando que todos los argumentos soporten la transmisión
  * Seleccionando un array de salida apropiado para el conjunto de argumentos dado
  * Seleccionando una implementación eficiente para el conjunto de argumentos dado

No todos los tipos admiten `axes` e indexación, pero muchos son convenientes para permitir en la difusión. La función [`Base.broadcastable`](@ref) se llama en cada argumento para la difusión, permitiendo que devuelva algo diferente que soporte `axes` e indexación. Por defecto, esta es la función identidad para todos los `AbstractArray`s y `Number`s: ya admiten `axes` e indexación.

Si un tipo está destinado a actuar como un "escalar de 0 dimensiones" (un solo objeto) en lugar de como un contenedor para la difusión, entonces se debe definir el siguiente método:

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

que devuelve el argumento envuelto en un contenedor [`Ref`](@ref) de 0 dimensiones. Por ejemplo, tal método de envoltura está definido para los tipos mismos, funciones, singleton especiales como [`missing`](@ref) y [`nothing`](@ref), y fechas.

Los tipos personalizados similares a arreglos pueden especializar `Base.broadcastable` para definir su forma, pero deben seguir la convención de que `collect(Base.broadcastable(x)) == collect(x)`. Una excepción notable es `AbstractString`; las cadenas se tratan de manera especial para comportarse como escalares a efectos de la difusión, aunque son colecciones iterables de sus caracteres (ver [Strings](@ref) para más información).

Los siguientes dos pasos (seleccionar el array de salida e implementación) dependen de determinar una única respuesta para un conjunto dado de argumentos. Broadcast debe tomar todos los tipos variados de sus argumentos y reducirlos a un solo array de salida y una sola implementación. Broadcast llama a esta única respuesta un "estilo". Cada objeto que se puede transmitir tiene su propio estilo preferido, y se utiliza un sistema similar a la promoción para combinar estos estilos en una única respuesta: el "estilo de destino".

### Broadcast Styles

`Base.BroadcastStyle` es el tipo abstracto del cual se derivan todos los estilos de transmisión. Cuando se usa como una función, tiene dos formas posibles: unaria (un solo argumento) y binaria. La variante unaria indica que tienes la intención de implementar un comportamiento de transmisión específico y/o un tipo de salida, y no deseas depender del valor predeterminado de respaldo [`Broadcast.DefaultArrayStyle`](@ref).

Para anular estos valores predeterminados, puedes definir un `BroadcastStyle` personalizado para tu objeto:

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

En algunos casos puede ser conveniente no tener que definir `MyStyle`, en cuyo caso puedes aprovechar uno de los envoltorios de difusión generales:

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()` se puede usar para tipos arbitrarios.
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()` se prefiere si `MyType` es un `AbstractArray`.
  * Para `AbstractArrays` que solo admiten una cierta dimensionalidad, crea un subtipo de `Broadcast.AbstractArrayStyle{N}` (ver abajo).

Cuando tu operación de transmisión involucra varios argumentos, los estilos de argumento individuales se combinan para determinar un único `DestStyle` que controla el tipo del contenedor de salida. Para más detalles, consulta [below](@ref writing-binary-broadcasting-rules).

### Selecting an appropriate output array

El estilo de difusión se calcula para cada operación de difusión para permitir la distribución y especialización. La asignación real del array de resultados es manejada por `similar`, utilizando el objeto Broadcasted como su primer argumento.

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

La definición de respaldo es

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

Sin embargo, si es necesario, puedes especializarte en cualquiera o en todos estos argumentos. El argumento final `bc` es una representación perezosa de una operación de difusión (potencialmente fusionada), un objeto `Broadcasted`. Para estos propósitos, los campos más importantes del envoltorio son `f` y `args`, que describen la función y la lista de argumentos, respectivamente. Ten en cuenta que la lista de argumentos puede —y a menudo lo hace— incluir otros envoltorios `Broadcasted` anidados.

Para un ejemplo completo, digamos que has creado un tipo, `ArrayAndChar`, que almacena un array y un solo carácter:

```jldoctest ArrayAndChar; output = false
struct ArrayAndChar{T,N} <: AbstractArray{T,N}
    data::Array{T,N}
    char::Char
end
Base.size(A::ArrayAndChar) = size(A.data)
Base.getindex(A::ArrayAndChar{T,N}, inds::Vararg{Int,N}) where {T,N} = A.data[inds...]
Base.setindex!(A::ArrayAndChar{T,N}, val, inds::Vararg{Int,N}) where {T,N} = A.data[inds...] = val
Base.showarg(io::IO, A::ArrayAndChar, toplevel) = print(io, typeof(A), " with char '", A.char, "'")
# output

```

Es posible que desees que la transmisión preserve los `char` "metadatos". Primero definimos

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

Esto significa que también debemos definir un método `similar` correspondiente:

```jldoctest ArrayAndChar; output = false
function Base.similar(bc::Broadcast.Broadcasted{Broadcast.ArrayStyle{ArrayAndChar}}, ::Type{ElType}) where ElType
    # Scan the inputs for the ArrayAndChar:
    A = find_aac(bc)
    # Use the char field of A to create the output
    ArrayAndChar(similar(Array{ElType}, axes(bc)), A.char)
end

"`A = find_aac(As)` returns the first ArrayAndChar among the arguments."
find_aac(bc::Base.Broadcast.Broadcasted) = find_aac(bc.args)
find_aac(args::Tuple) = find_aac(find_aac(args[1]), Base.tail(args))
find_aac(x) = x
find_aac(::Tuple{}) = nothing
find_aac(a::ArrayAndChar, rest) = a
find_aac(::Any, rest) = find_aac(rest)
# output
find_aac (generic function with 6 methods)
```

A partir de estas definiciones, se obtiene el siguiente comportamiento:

```jldoctest ArrayAndChar
julia> a = ArrayAndChar([1 2; 3 4], 'x')
2×2 ArrayAndChar{Int64, 2} with char 'x':
 1  2
 3  4

julia> a .+ 1
2×2 ArrayAndChar{Int64, 2} with char 'x':
 2  3
 4  5

julia> a .+ [5,10]
2×2 ArrayAndChar{Int64, 2} with char 'x':
  6   7
 13  14
```

### [Extending broadcast with custom implementations](@id extending-in-place-broadcast)

En general, una operación de difusión se representa mediante un contenedor `Broadcasted` perezoso que retiene la función que se aplicará junto con sus argumentos. Esos argumentos pueden ser a su vez contenedores `Broadcasted` más anidados, formando un gran árbol de expresiones que se evaluará. Un árbol anidado de contenedores `Broadcasted` se construye directamente mediante la sintaxis de punto implícita; `5 .+ 2.*x` se representa transitoriamente como `Broadcasted(+, 5, Broadcasted(*, 2, x))`, por ejemplo. Esto es invisible para los usuarios, ya que se realiza inmediatamente a través de una llamada a `copy`, pero es este contenedor el que proporciona la base para la extensibilidad de la difusión para los autores de tipos personalizados. La maquinaria de difusión incorporada determinará entonces el tipo y tamaño del resultado en función de los argumentos, lo asignará y finalmente copiará la realización del objeto `Broadcasted` en él con un método predeterminado `copyto!(::AbstractArray, ::Broadcasted)`. Los métodos de `broadcast` y `broadcast!` incorporados de respaldo construyen de manera similar una representación transitoria `Broadcasted` de la operación para que puedan seguir el mismo camino de código. Esto permite que las implementaciones de matrices personalizadas proporcionen su propia especialización de `copyto!` para personalizar y optimizar la difusión. Esto se determina nuevamente por el estilo de difusión calculado. Esta es una parte tan importante de la operación que se almacena como el primer parámetro de tipo del tipo `Broadcasted`, lo que permite la dispatch y la especialización.

Para algunos tipos, la maquinaria para "fusionar" operaciones a través de niveles anidados de difusión no está disponible o podría hacerse de manera más eficiente de forma incremental. En tales casos, es posible que necesite o desee evaluar `x .* (x .+ 1)` como si se hubiera escrito `broadcast(*, x, broadcast(+, x, 1))`, donde la operación interna se evalúa antes de abordar la operación externa. Este tipo de operación ansiosa es directamente soportada por un poco de indirecta; en lugar de construir directamente objetos `Broadcasted`, Julia reduce la expresión fusionada `x .* (x .+ 1)` a `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))`. Ahora, por defecto, `broadcasted` simplemente llama al constructor `Broadcasted` para crear la representación perezosa del árbol de expresión fusionada, pero puede elegir anularlo para una combinación particular de función y argumentos.

Como ejemplo, los objetos `AbstractRange` integrados utilizan esta maquinaria para optimizar partes de expresiones transmitidas que pueden evaluarse de manera anticipada puramente en términos de inicio, paso y longitud (o parada) en lugar de calcular cada elemento individual. Al igual que toda la otra maquinaria, `broadcasted` también calcula y expone el estilo de transmisión combinado de sus argumentos, por lo que en lugar de especializarse en `broadcasted(f, args...)`, puedes especializarte en `broadcasted(::DestStyle, f, args...)` para cualquier combinación de estilo, función y argumentos.

Por ejemplo, la siguiente definición admite la negación de rangos:

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

La difusión en el lugar puede ser soportada definiendo el método apropiado `copyto!(dest, bc::Broadcasted)`. Debido a que podrías querer especializarte ya sea en `dest` o en el subtipo específico de `bc`, para evitar ambigüedades entre paquetes, recomendamos la siguiente convención.

Si deseas especializarte en un estilo particular `DestStyle`, define un método para

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

Opcionalmente, con este formulario también puedes especializarte en el tipo de `dest`.

Si en su lugar desea especializarse en el tipo de destino `DestType` sin especializarse en `DestStyle`, entonces debe definir un método con la siguiente firma:

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

Esto aprovecha una implementación de respaldo de `copyto!` que convierte el envoltorio en un `Broadcasted{Nothing}`. En consecuencia, la especialización en `DestType` tiene una menor precedencia que los métodos que se especializan en `DestStyle`.

De manera similar, puedes anular completamente la transmisión fuera de lugar con un método `copy(::Broadcasted)`.

#### Working with `Broadcasted` objects

Para implementar un método `copy` o `copyto!`, por supuesto, debes trabajar con el envoltorio `Broadcasted` para calcular cada elemento. Hay dos formas principales de hacerlo:

  * `Broadcast.flatten` recomputa la operación potencialmente anidada en una sola función y una lista plana de argumentos. Eres responsable de implementar las reglas de forma de broadcasting tú mismo, pero esto puede ser útil en situaciones limitadas.
  * Iterando sobre los `CartesianIndices` de los `axes(::Broadcasted)` y utilizando la indexación con el objeto `CartesianIndex` resultante para calcular el resultado.

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

Las reglas de precedencia se definen mediante llamadas binarias `BroadcastStyle`:

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

donde `Style12` es el `BroadcastStyle` que deseas elegir para las salidas que involucran argumentos de `Style1` y `Style2`. Por ejemplo,

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

indica que `Tuple` "gana" sobre los arreglos de cero dimensiones (el contenedor de salida será una tupla). Vale la pena señalar que no necesitas (y no deberías) definir ambos órdenes de argumentos de esta llamada; definir uno es suficiente sin importar el orden en que el usuario suministre los argumentos.

Para los tipos `AbstractArray`, definir un `BroadcastStyle` reemplaza la elección por defecto, [`Broadcast.DefaultArrayStyle`](@ref). `DefaultArrayStyle` y el supertipo abstracto, `AbstractArrayStyle`, almacenan la dimensionalidad como un parámetro de tipo para soportar tipos de arreglos especializados que tienen requisitos de dimensionalidad fijos.

`DefaultArrayStyle` "pierde" ante cualquier otro `AbstractArrayStyle` que se haya definido debido a los siguientes métodos:

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

No necesitas escribir reglas de `BroadcastStyle` binarias a menos que desees establecer precedencia para dos o más tipos que no sean `DefaultArrayStyle`.

Si su tipo de matriz tiene requisitos de dimensionalidad fija, entonces debe subtipar `AbstractArrayStyle`. Por ejemplo, el código de matriz dispersa tiene las siguientes definiciones:

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

Siempre que subclasifiques `AbstractArrayStyle`, también necesitas definir reglas para combinar dimensionalidades, creando un constructor para tu estilo que tome un argumento `Val(N)`. Por ejemplo:

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

Estas reglas indican que la combinación de un `SparseVecStyle` con arreglos de 0 o 1 dimensión produce otro `SparseVecStyle`, que su combinación con un arreglo de 2 dimensiones produce un `SparseMatStyle`, y cualquier cosa de mayor dimensionalidad vuelve al marco denso de dimensiones arbitrarias. Estas reglas permiten que la transmisión mantenga la representación dispersa para operaciones que resultan en salidas de una o dos dimensiones, pero producen un `Array` para cualquier otra dimensionalidad.

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

A veces, es deseable cambiar cómo el usuario final interactúa con los campos de un objeto. En lugar de otorgar acceso directo a los campos de tipo, se puede proporcionar una capa adicional de abstracción entre el usuario y el código sobrecargando `object.field`. Las propiedades son lo que el usuario *ve de* el objeto, los campos lo que el objeto *realmente es*.

Por defecto, las propiedades y los campos son lo mismo. Sin embargo, este comportamiento se puede cambiar. Por ejemplo, toma esta representación de un punto en un plano en [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system):

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

Como se describe en la tabla anterior, el acceso por punto `p.r` es lo mismo que `getproperty(p, :r)`, que por defecto es lo mismo que `getfield(p, :r)`:

```jldoctest polartype
julia> propertynames(p)
(:r, :ϕ)

julia> getproperty(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)

julia> p.r, p.ϕ
(7.0, 0.7853981633974483)

julia> getfield(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)
```

Sin embargo, es posible que queramos que los usuarios no sean conscientes de que `Point` almacena las coordenadas como `r` y `ϕ` (campos), y en su lugar interactúen con `x` y `y` (propiedades). Los métodos en la primera columna se pueden definir para agregar nueva funcionalidad:

```jldoctest polartype
julia> Base.propertynames(::Point, private::Bool=false) = private ? (:x, :y, :r, :ϕ) : (:x, :y)

julia> function Base.getproperty(p::Point, s::Symbol)
           if s === :x
               return getfield(p, :r) * cos(getfield(p, :ϕ))
           elseif s === :y
               return getfield(p, :r) * sin(getfield(p, :ϕ))
           else
               # This allows accessing fields with p.r and p.ϕ
               return getfield(p, s)
           end
       end

julia> function Base.setproperty!(p::Point, s::Symbol, f)
           if s === :x
               y = p.y
               setfield!(p, :r, sqrt(f^2 + y^2))
               setfield!(p, :ϕ, atan(y, f))
               return f
           elseif s === :y
               x = p.x
               setfield!(p, :r, sqrt(x^2 + f^2))
               setfield!(p, :ϕ, atan(f, x))
               return f
           else
               # This allow modifying fields with p.r and p.ϕ
               return setfield!(p, s, f)
           end
       end
```

Es importante que `getfield` y `setfield` se utilicen dentro de `getproperty` y `setproperty!` en lugar de la sintaxis de punto, ya que la sintaxis de punto haría que las funciones fueran recursivas, lo que puede llevar a problemas de inferencia de tipos. Ahora podemos probar la nueva funcionalidad:

```jldoctest polartype
julia> propertynames(p)
(:x, :y)

julia> p.x
4.949747468305833

julia> p.y = 4.0
4.0

julia> p.r
6.363961030678928
```

Finalmente, vale la pena señalar que agregar propiedades de instancia de esta manera se hace bastante raramente en Julia y, en general, solo debe hacerse si hay una buena razón para hacerlo.

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

Para soportar el redondeo en un nuevo tipo, generalmente es suficiente definir el único método `round(x::ObjType, r::RoundingMode)`. El modo de redondeo pasado determina en qué dirección debe redondearse el valor. Los modos de redondeo más comúnmente utilizados son `RoundNearest`, `RoundToZero`, `RoundDown` y `RoundUp`, ya que estos modos de redondeo se utilizan en las definiciones del método de un argumento `round`, y `trunc`, `floor` y `ceil`, respectivamente.

En algunos casos, es posible definir un método `round` de tres argumentos que sea más preciso o eficiente que el método de dos argumentos seguido de la conversión. En este caso, es aceptable definir el método de tres argumentos además del método de dos argumentos. Si es imposible representar el resultado redondeado como un objeto del tipo `T`, entonces el método de tres argumentos debe lanzar un `InexactError`.

Por ejemplo, si tenemos un tipo `Interval` que representa un rango de valores posibles similar a https://github.com/JuliaPhysics/Measurements.jl, podemos definir el redondeo en ese tipo con lo siguiente

```jldoctest
julia> struct Interval{T}
           min::T
           max::T
       end

julia> Base.round(x::Interval, r::RoundingMode) = Interval(round(x.min, r), round(x.max, r))

julia> x = Interval(1.7, 2.2)
Interval{Float64}(1.7, 2.2)

julia> round(x)
Interval{Float64}(2.0, 2.0)

julia> floor(x)
Interval{Float64}(1.0, 2.0)

julia> ceil(x)
Interval{Float64}(2.0, 3.0)

julia> trunc(x)
Interval{Float64}(1.0, 2.0)
```
