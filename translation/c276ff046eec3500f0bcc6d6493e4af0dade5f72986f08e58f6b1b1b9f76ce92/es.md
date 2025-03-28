# [Single- and multi-dimensional Arrays](@id man-multi-dim-arrays)

Julia, al igual que la mayoría de los lenguajes de computación técnica, proporciona una implementación de arreglos de primera clase. La mayoría de los lenguajes de computación técnica prestan mucha atención a su implementación de arreglos a expensas de otros contenedores. Julia no trata los arreglos de ninguna manera especial. La biblioteca de arreglos está implementada casi completamente en Julia misma y deriva su rendimiento del compilador, al igual que cualquier otro código escrito en Julia. Como tal, también es posible definir tipos de arreglos personalizados heredando de [`AbstractArray`](@ref). Consulte el [manual section on the AbstractArray interface](@ref man-interface-array) para obtener más detalles sobre la implementación de un tipo de arreglo personalizado.

Un arreglo es una colección de objetos almacenados en una cuadrícula multidimensional. Se permiten arreglos de cero dimensiones, ver [this FAQ entry](@ref faq-array-0dim). En el caso más general, un arreglo puede contener objetos del tipo [`Any`](@ref). Para la mayoría de los propósitos computacionales, los arreglos deben contener objetos de un tipo más específico, como [`Float64`](@ref) o [`Int32`](@ref).

En general, a diferencia de muchos otros lenguajes de computación técnica, Julia no espera que los programas se escriban en un estilo vectorizado para obtener rendimiento. El compilador de Julia utiliza inferencia de tipos y genera código optimizado para la indexación de arreglos escalares, lo que permite que los programas se escriban en un estilo que es conveniente y legible, sin sacrificar rendimiento, y utilizando menos memoria en ocasiones.

En Julia, todos los argumentos de las funciones son [passed by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing) (es decir, por punteros). Algunos lenguajes de computación técnica pasan arreglos por valor, y aunque esto previene la modificación accidental por parte de los llamados de un valor en el llamador, dificulta evitar la copia no deseada de arreglos. Por convención, un nombre de función que termina con un `!` indica que mutará o destruirá el valor de uno o más de sus argumentos (compara, por ejemplo, [`sort`](@ref) y [`sort!`](@ref)). Los llamados deben hacer copias explícitas para asegurarse de que no modifican entradas que no tienen la intención de cambiar. Muchas funciones no mutantes se implementan llamando a una función del mismo nombre con un `!` añadido al final sobre una copia explícita de la entrada, y devolviendo esa copia.

## Basic Functions

| Function               | Description                                                                      |
|:---------------------- |:-------------------------------------------------------------------------------- |
| [`eltype(A)`](@ref)    | the type of the elements contained in `A`                                        |
| [`length(A)`](@ref)    | the number of elements in `A`                                                    |
| [`ndims(A)`](@ref)     | the number of dimensions of `A`                                                  |
| [`size(A)`](@ref)      | a tuple containing the dimensions of `A`                                         |
| [`size(A,n)`](@ref)    | the size of `A` along dimension `n`                                              |
| [`axes(A)`](@ref)      | a tuple containing the valid indices of `A`                                      |
| [`axes(A,n)`](@ref)    | a range expressing the valid indices along dimension `n`                         |
| [`eachindex(A)`](@ref) | an efficient iterator for visiting each position in `A`                          |
| [`stride(A,k)`](@ref)  | the stride (linear index distance between adjacent elements) along dimension `k` |
| [`strides(A)`](@ref)   | a tuple of the strides in each dimension                                         |

## Construction and Initialization

Many functions for constructing and initializing arrays are provided. In the following list of such functions, calls with a `dims...` argument can either take a single tuple of dimension sizes or a series of dimension sizes passed as a variable number of arguments. Most of these functions also accept a first input `T`, which is the element type of the array. If the type `T` is omitted it will default to [`Float64`](@ref).

| Function                           | Description                                                                                                                                                                                                                                  |
|:---------------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Array{T}(undef, dims...)`](@ref) | an uninitialized dense [`Array`](@ref)                                                                                                                                                                                                       |
| [`zeros(T, dims...)`](@ref)        | an `Array` of all zeros                                                                                                                                                                                                                      |
| [`ones(T, dims...)`](@ref)         | an `Array` of all ones                                                                                                                                                                                                                       |
| [`trues(dims...)`](@ref)           | a [`BitArray`](@ref) with all values `true`                                                                                                                                                                                                  |
| [`falses(dims...)`](@ref)          | a `BitArray` with all values `false`                                                                                                                                                                                                         |
| [`reshape(A, dims...)`](@ref)      | an array containing the same data as `A`, but with different dimensions                                                                                                                                                                      |
| [`copy(A)`](@ref)                  | copy `A`                                                                                                                                                                                                                                     |
| [`deepcopy(A)`](@ref)              | copy `A`, recursively copying its elements                                                                                                                                                                                                   |
| [`similar(A, T, dims...)`](@ref)   | an uninitialized array of the same type as `A` (dense, sparse, etc.), but with the specified element type and dimensions. The second and third arguments are both optional, defaulting to the element type and dimensions of `A` if omitted. |
| [`reinterpret(T, A)`](@ref)        | an array with the same binary data as `A`, but with element type `T`                                                                                                                                                                         |
| [`rand(T, dims...)`](@ref)         | an `Array` with random, iid [^1] and uniformly distributed values. For floating point types `T`, the values lie in the half-open interval $[0, 1)$.                                                                                          |
| [`randn(T, dims...)`](@ref)        | an `Array` with random, iid and standard normally distributed values                                                                                                                                                                         |
| [`Matrix{T}(I, m, n)`](@ref)       | `m`-by-`n` identity matrix. Requires `using LinearAlgebra` for [`I`](@ref).                                                                                                                                                                  |
| [`range(start, stop, n)`](@ref)    | a range of `n` linearly spaced elements from `start` to `stop`                                                                                                                                                                               |
| [`fill!(A, x)`](@ref)              | fill the array `A` with the value `x`                                                                                                                                                                                                        |
| [`fill(x, dims...)`](@ref)         | an `Array` filled with the value `x`. In particular, `fill(x)` constructs a zero-dimensional `Array` containing `x`.                                                                                                                         |

[^1]: *iid*, independently and identically distributed.

Para ver las diversas formas en que podemos pasar dimensiones a estas funciones, considera los siguientes ejemplos:

```jldoctest
julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros(Int8, (2, 3))
2×3 Matrix{Int8}:
 0  0  0
 0  0  0

julia> zeros((2, 3))
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
```

Aquí, `(2, 3)` es un [`Tuple`](@ref) y el primer argumento — el tipo de elemento — es opcional, con un valor predeterminado de `Float64`.

## [Array literals](@id man-array-literals)

Los arreglos también se pueden construir directamente con corchetes cuadrados; la sintaxis `[A, B, C, ...]` crea un arreglo unidimensional (es decir, un vector) que contiene los argumentos separados por comas como sus elementos. El tipo de elemento ([`eltype`](@ref)) del arreglo resultante se determina automáticamente por los tipos de los argumentos dentro de los corchetes. Si todos los argumentos son del mismo tipo, entonces ese es su `eltype`. Si todos tienen un [promotion type](@ref conversion-and-promotion) común, entonces se convierten a ese tipo usando [`convert`](@ref) y ese tipo es el `eltype` del arreglo. De lo contrario, se construye un arreglo heterogéneo que puede contener cualquier cosa — un `Vector{Any}` — esto incluye el literal `[]` donde no se dan argumentos. [Array literal can be typed](@ref man-array-typed-literal) con la sintaxis `T[A, B, C, ...]` donde `T` es un tipo.

```jldoctest
julia> [1, 2, 3] # An array of `Int`s
3-element Vector{Int64}:
 1
 2
 3

julia> promote(1, 2.3, 4//5) # This combination of Int, Float64 and Rational promotes to Float64
(1.0, 2.3, 0.8)

julia> [1, 2.3, 4//5] # Thus that's the element type of this Array
3-element Vector{Float64}:
 1.0
 2.3
 0.8

julia> Float32[1, 2.3, 4//5] # Specify element type manually
3-element Vector{Float32}:
 1.0
 2.3
 0.8

julia> []
Any[]
```

### [Concatenation](@id man-array-concatenation)

Si los argumentos dentro de los corchetes están separados por punto y coma (`;`) o saltos de línea en lugar de comas, entonces su contenido se *concatena verticalmente* en lugar de que los argumentos se utilicen como elementos en sí mismos.

```jldoctest
julia> [1:2, 4:5] # Has a comma, so no concatenation occurs. The ranges are themselves the elements
2-element Vector{UnitRange{Int64}}:
 1:2
 4:5

julia> [1:2; 4:5]
4-element Vector{Int64}:
 1
 2
 4
 5

julia> [1:2
        4:5
        6]
5-element Vector{Int64}:
 1
 2
 4
 5
 6
```

De manera similar, si los argumentos están separados por tabulaciones, espacios o punto y coma doble, entonces su contenido se *concatena horizontalmente* juntos.

```jldoctest
julia> [1:2  4:5  7:8]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [[1,2]  [4,5]  [7,8]]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> [1 2 3] # Numbers can also be horizontally concatenated
1×3 Matrix{Int64}:
 1  2  3

julia> [1;; 2;; 3;; 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Los punto y coma simples (o saltos de línea) y los espacios (o tabulaciones) se pueden combinar para concatenar tanto horizontal como verticalmente al mismo tiempo.

```jldoctest
julia> [1 2
        3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> [zeros(Int, 2, 2) [1; 2]
        [3 4]            5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [[1 1]; 2 3; [4 4]]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Los espacios (y tabulaciones) tienen una precedencia más alta que los puntos y comas, realizando primero cualquier concatenación horizontal y luego concatenando el resultado. Usar dobles puntos y comas para la concatenación horizontal, por otro lado, realiza cualquier concatenación vertical antes de concatenar horizontalmente el resultado.

```jldoctest
julia> [zeros(Int, 2, 2) ; [3 4] ;; [1; 2] ; 5]
3×3 Matrix{Int64}:
 0  0  1
 0  0  2
 3  4  5

julia> [1:2; 4;; 1; 3:4]
3×2 Matrix{Int64}:
 1  1
 2  3
 4  4
```

Así como `;` y `;;` se concatenan en la primera y segunda dimensión, usar más punto y coma extiende este mismo esquema general. El número de punto y coma en el separador especifica la dimensión particular, por lo que `;;;` se concatena en la tercera dimensión, `;;;;` en la cuarta, y así sucesivamente. Menos punto y coma tienen prioridad, por lo que las dimensiones inferiores generalmente se concatenan primero.

```jldoctest
julia> [1; 2;; 3; 4;; 5; 6;;;
        7; 8;; 9; 10;; 11; 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

Como antes, los espacios (y tabulaciones) para la concatenación horizontal tienen una mayor precedencia que cualquier número de punto y coma. Así, los arreglos de mayor dimensión también se pueden escribir especificando sus filas primero, con sus elementos dispuestos textualmente de una manera similar a su disposición:

```jldoctest
julia> [1 3 5
        2 4 6;;;
        7 9 11
        8 10 12]
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> [1 2;;; 3 4;;;; 5 6;;; 7 8]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8

julia> [[1 2;;; 3 4];;;; [5 6];;; [7 8]]
1×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  2

[:, :, 2, 1] =
 3  4

[:, :, 1, 2] =
 5  6

[:, :, 2, 2] =
 7  8
```

Aunque ambos significan concatenación en la segunda dimensión, los espacios (o tabulaciones) y `;;` no pueden aparecer en la misma expresión de matriz a menos que el punto y coma doble simplemente esté sirviendo como un carácter de "continuación de línea". Esto permite que una única concatenación horizontal se extienda a través de múltiples líneas (sin que el salto de línea sea interpretado como una concatenación vertical).

```jldoctest
julia> [1 2 ;;
       3 4]
1×4 Matrix{Int64}:
 1  2  3  4
```

Los puntos y comas de terminación también se pueden usar para agregar dimensiones de longitud 1 al final.

```jldoctest
julia> [1;;]
1×1 Matrix{Int64}:
 1

julia> [2; 3;;;]
2×1×1 Array{Int64, 3}:
[:, :, 1] =
 2
 3
```

Más generalmente, la concatenación se puede lograr a través de la función [`cat`](@ref). Estas sintaxis son abreviaturas para llamadas a funciones que en sí mismas son funciones de conveniencia:

| Syntax                 | Function         | Description                                                                                                |
|:---------------------- |:---------------- |:---------------------------------------------------------------------------------------------------------- |
|                        | [`cat`](@ref)    | concatenate input arrays along dimension(s) `k`                                                            |
| `[A; B; C; ...]`       | [`vcat`](@ref)   | shorthand for `cat(A...; dims=1)`                                                                          |
| `[A B C ...]`          | [`hcat`](@ref)   | shorthand for `cat(A...; dims=2)`                                                                          |
| `[A B; C D; ...]`      | [`hvcat`](@ref)  | simultaneous vertical and horizontal concatenation                                                         |
| `[A; C;; B; D;;; ...]` | [`hvncat`](@ref) | simultaneous n-dimensional concatenation, where number of semicolons indicate the dimension to concatenate |

### [Typed array literals](@id man-array-typed-literal)

Un arreglo con un tipo de elemento específico se puede construir utilizando la sintaxis `T[A, B, C, ...]`. Esto construirá un arreglo unidimensional con el tipo de elemento `T`, inicializado para contener elementos `A`, `B`, `C`, etc. Por ejemplo, `Any[x, y, z]` construye un arreglo heterogéneo que puede contener cualquier valor.

La sintaxis de concatenación también puede ser precedida por un tipo para especificar el tipo de elemento del resultado.

```jldoctest
julia> [[1 2] [3 4]]
1×4 Matrix{Int64}:
 1  2  3  4

julia> Int8[[1 2] [3 4]]
1×4 Matrix{Int8}:
 1  2  3  4
```

## [Comprehensions](@id man-comprehensions)

Las comprensiones proporcionan una forma general y poderosa de construir arreglos. La sintaxis de comprensión es similar a la notación de construcción de conjuntos en matemáticas:

```
A = [ F(x, y, ...) for x=rx, y=ry, ... ]
```

El significado de esta forma es que `F(x,y,...)` se evalúa con las variables `x`, `y`, etc. tomando cada valor en su lista de valores dada. Los valores pueden especificarse como cualquier objeto iterable, pero comúnmente serán rangos como `1:n` o `2:(n-1)`, o arreglos explícitos de valores como `[1.2, 3.4, 5.7]`. El resultado es un arreglo denso N-d con dimensiones que son la concatenación de las dimensiones de los rangos de variables `rx`, `ry`, etc. y cada evaluación de `F(x,y,...)` devuelve un escalar.

El siguiente ejemplo calcula un promedio ponderado del elemento actual y su vecino izquierdo y derecho a lo largo de una cuadrícula unidimensional. :

```julia-repl
julia> x = rand(8)
8-element Array{Float64,1}:
 0.843025
 0.869052
 0.365105
 0.699456
 0.977653
 0.994953
 0.41084
 0.809411

julia> [ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
6-element Array{Float64,1}:
 0.736559
 0.57468
 0.685417
 0.912429
 0.8446
 0.656511
```

El tipo de array resultante depende de los tipos de los elementos computados, al igual que [array literals](@ref man-array-literals). Para controlar el tipo de manera explícita, se puede anteponer un tipo a la comprensión. Por ejemplo, podríamos haber solicitado el resultado en precisión simple escribiendo:

```julia
Float32[ 0.25*x[i-1] + 0.5*x[i] + 0.25*x[i+1] for i=2:length(x)-1 ]
```

## [Generator Expressions](@id man-generators)

Las comprensiones también se pueden escribir sin los corchetes cuadrados que las encierran, produciendo un objeto conocido como un generador. Este objeto se puede iterar para producir valores bajo demanda, en lugar de asignar un arreglo y almacenarlos por adelantado (ver [Iteration](@ref)). Por ejemplo, la siguiente expresión suma una serie sin asignar memoria:

```jldoctest
julia> sum(1/n^2 for n=1:1000)
1.6439345666815615
```

Al escribir una expresión generadora con múltiples dimensiones dentro de una lista de argumentos, se necesitan paréntesis para separar el generador de los argumentos subsiguientes:

```julia-repl
julia> map(tuple, 1/(i+j) for i=1:2, j=1:2, [1:4;])
ERROR: syntax: invalid iteration specification
```

Todas las expresiones separadas por comas después de `for` se interpretan como rangos. Agregar paréntesis nos permite añadir un tercer argumento a [`map`](@ref):

```jldoctest
julia> map(tuple, (1/(i+j) for i=1:2, j=1:2), [1 3; 2 4])
2×2 Matrix{Tuple{Float64, Int64}}:
 (0.5, 1)       (0.333333, 3)
 (0.333333, 2)  (0.25, 4)
```

Los generadores se implementan a través de funciones internas. Al igual que las funciones internas utilizadas en otras partes del lenguaje, las variables del ámbito que las rodea pueden ser "capturadas" en la función interna. Por ejemplo, `sum(p[i] - q[i] for i=1:n)` captura las tres variables `p`, `q` y `n` del ámbito que las rodea. Las variables capturadas pueden presentar desafíos de rendimiento; consulta [performance tips](@ref man-performance-captured).

Los rangos en generadores y comprensiones pueden depender de rangos anteriores escribiendo múltiples palabras clave `for`:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i]
6-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (2, 2)
 (3, 1)
 (3, 2)
 (3, 3)
```

En tales casos, el resultado es siempre 1-d.

Los valores generados se pueden filtrar utilizando la palabra clave `if`:

```jldoctest
julia> [(i, j) for i=1:3 for j=1:i if i+j == 4]
2-element Vector{Tuple{Int64, Int64}}:
 (2, 2)
 (3, 1)
```

## [Indexing](@id man-array-indexing)

La sintaxis general para indexar en un arreglo n-dimensional `A` es:

```
X = A[I_1, I_2, ..., I_n]
```

donde cada `I_k` puede ser un entero escalar, un arreglo de enteros, o cualquier otro [supported index](@ref man-supported-index-types). Esto incluye [`Colon`](@ref) (`:`) para seleccionar todos los índices dentro de toda la dimensión, rangos de la forma `a:c` o `a:b:c` para seleccionar subsecciones contiguas o estriadas, y arreglos de booleanos para seleccionar elementos en sus índices `true`.

Si todos los índices son escalares, entonces el resultado `X` es un solo elemento del arreglo `A`. De lo contrario, `X` es un arreglo con el mismo número de dimensiones que la suma de las dimensionalidades de todos los índices.

Si todos los índices `I_k` son vectores, por ejemplo, entonces la forma de `X` sería `(length(I_1), length(I_2), ..., length(I_n))`, con la ubicación `i_1, i_2, ..., i_n` de `X` conteniendo el valor `A[I_1[i_1], I_2[i_2], ..., I_n[i_n]]`.

Ejemplo:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[1, 2, 1, 1] # all scalar indices
3

julia> A[[1, 2], [1], [1, 2], [1]] # all vector indices
2×1×2×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1
 2

[:, :, 2, 1] =
 5
 6

julia> A[[1, 2], [1], [1, 2], 1] # a mix of index types
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 5
 6
```

Nota cómo el tamaño del array resultante es diferente en los últimos dos casos.

Si `I_1` se cambia a una matriz bidimensional, entonces `X` se convierte en un arreglo de `n+1` dimensiones con forma `(size(I_1, 1), size(I_1, 2), length(I_2), ..., length(I_n))`. La matriz añade una dimensión.

Ejemplo:

```jldoctest
julia> A = reshape(collect(1:16), (2, 2, 2, 2));

julia> A[[1 2; 1 2]]
2×2 Matrix{Int64}:
 1  2
 1  2

julia> A[[1 2; 1 2], 1, 2, 1]
2×2 Matrix{Int64}:
 5  6
 5  6
```

La ubicación `i_1, i_2, i_3, ..., i_{n+1}` contiene el valor en `A[I_1[i_1, i_2], I_2[i_3], ..., I_n[i_{n+1}]]`. Todas las dimensiones indexadas con escalares se eliminan. Por ejemplo, si `J` es un arreglo de índices, entonces el resultado de `A[2, J, 3]` es un arreglo con tamaño `size(J)`. Su elemento `j`-ésimo se llena con `A[2, J[j], 3]`.

Como parte especial de esta sintaxis, la palabra clave `end` puede usarse para representar el último índice de cada dimensión dentro de los corchetes de indexación, según lo determinado por el tamaño del arreglo más interno que se está indexando. La sintaxis de indexación sin la palabra clave `end` es equivalente a una llamada a [`getindex`](@ref):

```
X = getindex(A, I_1, I_2, ..., I_n)
```

Ejemplo:

```jldoctest
julia> x = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> x[2:3, 2:end-1]
2×2 Matrix{Int64}:
 6  10
 7  11

julia> x[1, [2 3; 4 1]]
2×2 Matrix{Int64}:
  5  9
 13  1
```

## [Indexed Assignment](@id man-indexed-assignment)

La sintaxis general para asignar valores en un arreglo n-dimensional `A` es:

```
A[I_1, I_2, ..., I_n] = X
```

donde cada `I_k` puede ser un entero escalar, un arreglo de enteros, o cualquier otro [supported index](@ref man-supported-index-types). Esto incluye [`Colon`](@ref) (`:`) para seleccionar todos los índices dentro de toda la dimensión, rangos de la forma `a:c` o `a:b:c` para seleccionar subsecciones contiguas o estriadas, y arreglos de booleanos para seleccionar elementos en sus índices `true`.

Si todos los índices `I_k` son enteros, entonces el valor en la ubicación `I_1, I_2, ..., I_n` de `A` se sobrescribe con el valor de `X`, [`convert`](@ref)ing al [`eltype`](@ref) de `A` si es necesario.

Si algún índice `I_k` es en sí mismo un arreglo, entonces el lado derecho `X` también debe ser un arreglo con la misma forma que el resultado de indexar `A[I_1, I_2, ..., I_n]` o un vector con el mismo número de elementos. El valor en la ubicación `I_1[i_1], I_2[i_2], ..., I_n[i_n]` de `A` se sobrescribe con el valor `X[i_1, i_2, ..., i_n]`, convirtiendo si es necesario. El operador de asignación elemento a elemento `.=` puede ser utilizado para [broadcast](@ref Broadcasting) `X` a través de las ubicaciones seleccionadas:

```
A[I_1, I_2, ..., I_n] .= X
```

Así como en [Indexing](@ref man-array-indexing), la palabra clave `end` puede usarse para representar el último índice de cada dimensión dentro de los corchetes de indexación, según lo determinado por el tamaño del arreglo en el que se está asignando. La sintaxis de asignación indexada sin la palabra clave `end` es equivalente a una llamada a [`setindex!`](@ref):

```
setindex!(A, X, I_1, I_2, ..., I_n)
```

Ejemplo:

```jldoctest
julia> x = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> x[3, 3] = -9;

julia> x[1:2, 1:2] = [-1 -4; -2 -5];

julia> x
3×3 Matrix{Int64}:
 -1  -4   7
 -2  -5   8
  3   6  -9
```

## [Supported index types](@id man-supported-index-types)

En la expresión `A[I_1, I_2, ..., I_n]`, cada `I_k` puede ser un índice escalar, un arreglo de índices escalares, o un objeto que representa un arreglo de índices escalares y puede ser convertido a tal por [`to_indices`](@ref):

1. Un índice escalar. Por defecto, esto incluye:

      * Números enteros no booleanos
      * [`CartesianIndex{N}`](@ref)s, que se comportan como un `N`-tupla de enteros que abarcan múltiples dimensiones (ver más detalles a continuación)
2. Un arreglo de índices escalares. Esto incluye:

      * Vectores y arreglos multidimensionales de enteros
      * Arreglos vacíos como `[]`, que no seleccionan elementos e.g. `A[[]]` (no debe confundirse con `A[]`)
      * Rangos como `a:c` o `a:b:c`, que seleccionan subsecciones contiguas o con pasos desde `a` hasta `c` (inclusive)
      * Cualquier arreglo personalizado de índices escalares que sea un subtipo de `AbstractArray`
      * Arreglos de `CartesianIndex{N}` (ver más detalles a continuación)
3. Un objeto que representa un arreglo de índices escalares y puede ser convertido a tal por [`to_indices`](@ref). Por defecto, esto incluye:

      * [`Colon()`](@ref) (`:`), que representa todos los índices dentro de una dimensión completa o a través de toda la matriz
      * Arreglos de booleanos, que seleccionan elementos en sus índices `true` (ver más detalles a continuación)

Algunos ejemplos:

```jldoctest
julia> A = reshape(collect(1:2:18), (3, 3))
3×3 Matrix{Int64}:
 1   7  13
 3   9  15
 5  11  17

julia> A[4]
7

julia> A[[2, 5, 8]]
3-element Vector{Int64}:
  3
  9
 15

julia> A[[1 4; 3 8]]
2×2 Matrix{Int64}:
 1   7
 5  15

julia> A[[]]
Int64[]

julia> A[1:2:5]
3-element Vector{Int64}:
 1
 5
 9

julia> A[2, :]
3-element Vector{Int64}:
  3
  9
 15

julia> A[:, 3]
3-element Vector{Int64}:
 13
 15
 17

julia> A[:, 3:3]
3×1 Matrix{Int64}:
 13
 15
 17
```

### Cartesian indices

El objeto especial `CartesianIndex{N}` representa un índice escalar que se comporta como una tupla `N` de enteros que abarca múltiples dimensiones. Por ejemplo:

```jldoctest cartesianindex
julia> A = reshape(1:32, 4, 4, 2);

julia> A[3, 2, 1]
7

julia> A[CartesianIndex(3, 2, 1)] == A[3, 2, 1] == 7
true
```

Considerado solo, esto puede parecer relativamente trivial; `CartesianIndex` simplemente reúne múltiples enteros en un solo objeto que representa un único índice multidimensional. Sin embargo, cuando se combina con otras formas de indexación e iteradores que producen `CartesianIndex`es, esto puede generar un código muy elegante y eficiente. Vea [Iteration](@ref) a continuación, y para algunos ejemplos más avanzados, consulte [this blog post on multidimensional algorithms and iteration](https://julialang.org/blog/2016/02/iteration).

Los arreglos de `CartesianIndex{N}` también son compatibles. Representan una colección de índices escalares que abarcan `N` dimensiones, lo que permite una forma de indexación que a veces se denomina indexación punto a punto. Por ejemplo, permite acceder a los elementos diagonales de la primera "página" de `A` desde arriba:

```jldoctest cartesianindex
julia> page = A[:, :, 1]
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> page[[CartesianIndex(1, 1),
             CartesianIndex(2, 2),
             CartesianIndex(3, 3),
             CartesianIndex(4, 4)]]
4-element Vector{Int64}:
  1
  6
 11
 16
```

Esto se puede expresar de manera mucho más simple con [dot broadcasting](@ref man-vectorized) y combinándolo con un índice entero normal (en lugar de extraer la primera `page` de `A` como un paso separado). Incluso se puede combinar con un `:` para extraer ambas diagonales de las dos páginas al mismo tiempo:

```jldoctest cartesianindex
julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), 1]
4-element Vector{Int64}:
  1
  6
 11
 16

julia> A[CartesianIndex.(axes(A, 1), axes(A, 2)), :]
4×2 Matrix{Int64}:
  1  17
  6  22
 11  27
 16  32
```

!!! warning
    `CartesianIndex` y arreglos de `CartesianIndex` no son compatibles con la palabra clave `end` para representar el último índice de una dimensión. No utilice `end` en expresiones de indexación que puedan contener `CartesianIndex` o arreglos de este tipo.


### Logical indexing

A menudo se refiere a esto como indexación lógica o indexación con una máscara lógica; la indexación mediante un arreglo booleano selecciona elementos en los índices donde sus valores son `true`. La indexación mediante un vector booleano `B` es efectivamente lo mismo que la indexación mediante el vector de enteros que se devuelve por [`findall(B)`](@ref). De manera similar, la indexación mediante un arreglo booleano de `N` dimensiones es efectivamente lo mismo que la indexación mediante el vector de `CartesianIndex{N}` donde sus valores son `true`. Un índice lógico debe ser un arreglo de la misma forma que la(s) dimensión(es) en la(s) que indexa, o debe ser el único índice proporcionado y coincidir con la forma de la vista unidimensional reestructurada del arreglo en el que indexa. En general, es más eficiente usar arreglos booleanos como índices directamente en lugar de llamar primero a [`findall`](@ref).

```jldoctest
julia> x = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> x[:, [true false; false true; true false]]
2×3 Matrix{Int64}:
 1  5   9
 2  6  10

julia> mask = map(ispow2, x)
2×3×2 Array{Bool, 3}:
[:, :, 1] =
 1  0  0
 1  1  0

[:, :, 2] =
 0  0  0
 1  0  0

julia> x[mask]
4-element Vector{Int64}:
 1
 2
 4
 8

julia> x[vec(mask)] == x[mask] # we can also index with a single Boolean vector
true
```

### Number of indices

#### Cartesian indexing

La forma ordinaria de indexar en un arreglo de `N` dimensiones es usar exactamente `N` índices; cada índice selecciona la(s) posición(es) en su dimensión particular. Por ejemplo, en el arreglo tridimensional `A = rand(4, 3, 2)`, `A[2, 3, 1]` seleccionará el número en la segunda fila de la tercera columna en la primera "página" del arreglo. Esto a menudo se denomina *indexación cartesiana*.

#### Linear indexing

Cuando se proporciona exactamente un índice `i`, ese índice ya no representa una ubicación en una dimensión particular de la matriz. En su lugar, selecciona el elemento `i` utilizando el orden de iteración por columnas que abarca linealmente toda la matriz. Esto se conoce como *indexación lineal*. Esencialmente, trata la matriz como si hubiera sido remodelada en un vector unidimensional con [`vec`](@ref).

```jldoctest linindexing
julia> A = [2 6; 4 7; 3 1]
3×2 Matrix{Int64}:
 2  6
 4  7
 3  1

julia> A[5]
7

julia> vec(A)[5]
7
```

Un índice lineal en el arreglo `A` se puede convertir a un `CartesianIndex` para indexación cartesiana con `CartesianIndices(A)[i]` (ver [`CartesianIndices`](@ref)), y un conjunto de `N` índices cartesianos se puede convertir a un índice lineal con `LinearIndices(A)[i_1, i_2, ..., i_N]` (ver [`LinearIndices`](@ref)).

```jldoctest linindexing
julia> CartesianIndices(A)[5]
CartesianIndex(2, 2)

julia> LinearIndices(A)[2, 2]
5
```

Es importante notar que hay una asimetría muy grande en el rendimiento de estas conversiones. Convertir un índice lineal a un conjunto de índices cartesianos requiere dividir y tomar el resto, mientras que ir en la otra dirección solo implica multiplicar y sumar. En los procesadores modernos, la división entera puede ser de 10 a 50 veces más lenta que la multiplicación. Mientras que algunos arreglos — como [`Array`](@ref) — están implementados utilizando un bloque lineal de memoria y utilizan directamente un índice lineal en sus implementaciones, otros arreglos — como [`Diagonal`](@ref) — necesitan el conjunto completo de índices cartesianos para realizar su búsqueda (ver [`IndexStyle`](@ref) para introspeccionar cuál es cuál).

!!! warning
    Al iterar sobre todos los índices de un arreglo, es mejor iterar sobre [`eachindex(A)`](@ref) en lugar de `1:length(A)`. No solo será más rápido en casos donde `A` es `IndexCartesian`, sino que también soportará arreglos con indexación personalizada, como [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl). Si solo se necesitan los valores, entonces es mejor iterar directamente el arreglo, es decir, `for a in A`.


#### Omitted and extra indices

Además de la indexación lineal, un array de `N` dimensiones puede ser indexado con menos o más de `N` índices en ciertas situaciones.

Los índices pueden omitirse si las dimensiones finales que no se indexan tienen todas longitud uno. En otras palabras, los índices finales solo se pueden omitir si hay un solo valor posible que esos índices omitidos podrían tener para una expresión de indexación dentro de los límites. Por ejemplo, un arreglo de cuatro dimensiones con tamaño `(3, 4, 2, 1)` puede ser indexado con solo tres índices, ya que la dimensión que se omite (la cuarta dimensión) tiene longitud uno. Tenga en cuenta que la indexación lineal tiene prioridad sobre esta regla.

```jldoctest
julia> A = reshape(1:24, 3, 4, 2, 1)
3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64:
[:, :, 1, 1] =
 1  4  7  10
 2  5  8  11
 3  6  9  12

[:, :, 2, 1] =
 13  16  19  22
 14  17  20  23
 15  18  21  24

julia> A[1, 3, 2] # Omits the fourth dimension (length 1)
19

julia> A[1, 3] # Attempts to omit dimensions 3 & 4 (lengths 2 and 1)
ERROR: BoundsError: attempt to access 3×4×2×1 reshape(::UnitRange{Int64}, 3, 4, 2, 1) with eltype Int64 at index [1, 3]

julia> A[19] # Linear indexing
19
```

Al omitir *todos* los índices con `A[]`, esta semántica proporciona un idiomático simple para recuperar el único elemento en un arreglo y al mismo tiempo asegurar que solo había un elemento.

De manera similar, se pueden proporcionar más de `N` índices si todos los índices más allá de la dimensionalidad del arreglo son `1` (o, más generalmente, son el primer y único elemento de `axes(A, d)` donde `d` es ese número de dimensión particular). Esto permite que los vectores sean indexados como matrices de una columna, por ejemplo:

```jldoctest
julia> A = [8, 6, 7]
3-element Vector{Int64}:
 8
 6
 7

julia> A[2, 1]
6
```

## Iteration

Las formas recomendadas de iterar sobre un array completo son

```julia
for a in A
    # Do something with the element a
end

for i in eachindex(A)
    # Do something with i and/or A[i]
end
```

El primer constructo se utiliza cuando necesitas el valor, pero no el índice, de cada elemento. En el segundo constructo, `i` será un `Int` si `A` es un tipo de arreglo con indexación lineal rápida; de lo contrario, será un `CartesianIndex`:

```jldoctest
julia> A = rand(4, 3);

julia> B = view(A, 1:3, 2:3);

julia> for i in eachindex(B)
           @show i
       end
i = CartesianIndex(1, 1)
i = CartesianIndex(2, 1)
i = CartesianIndex(3, 1)
i = CartesianIndex(1, 2)
i = CartesianIndex(2, 2)
i = CartesianIndex(3, 2)
```

!!! note
    En contraste con `for i = 1:length(A)`, iterar con [`eachindex`](@ref) proporciona una forma eficiente de iterar sobre cualquier tipo de arreglo. Además, esto también admite arreglos genéricos con indexación personalizada como [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl).


## Array traits

Si escribes un tipo personalizado [`AbstractArray`](@ref), puedes especificar que tiene indexación lineal rápida usando

```julia
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

Esta configuración hará que la iteración `eachindex` sobre un `MyArray` use enteros. Si no especificas este rasgo, se utilizará el valor predeterminado `IndexCartesian()`.

## [Array and Vectorized Operators and Functions](@id man-array-and-vectorized-operators-and-functions)

Los siguientes operadores son compatibles con los arreglos:

1. Aritmética unaria – `-`, `+`
2. Aritmética binaria – `-`, `+`, `*`, `/`, `\`, `^`
3. Comparación – `==`, `!=`, `≈` ([`isapprox`](@ref)), `≉`

Para habilitar la vectorización conveniente de operaciones matemáticas y otras, Julia [provides the dot syntax](@ref man-vectorized) `f.(args...)`, por ejemplo `sin.(x)` o `min.(x, y)`, para operaciones elemento a elemento sobre arreglos o mezclas de arreglos y escalares (una operación [Broadcasting](@ref)); estas tienen la ventaja adicional de "fusionarse" en un solo bucle cuando se combinan con otras llamadas de punto, por ejemplo `sin.(cos.(x))`.

También, *cada* operador binario soporta un [dot version](@ref man-dot-operators) que se puede aplicar a arreglos (y combinaciones de arreglos y escalares) en tal [fused broadcasting operations](@ref man-vectorized), p. ej. `z .== sin.(x .* y)`.

Tenga en cuenta que comparaciones como `==` operan en matrices completas, dando una única respuesta booleana. Use operadores de punto como `.==` para comparaciones elemento a elemento. (Para operaciones de comparación como `<`, *solo* la versión elemento a elemento `.<` es aplicable a matrices.)

También nota la diferencia entre `max.(a,b)`, que [`broadcast`](@ref) [`max`](@ref) elemento a elemento sobre `a` y `b`, y [`maximum(a)`](@ref), que encuentra el valor más grande dentro de `a`. La misma relación se mantiene para `min.(a, b)` y `minimum(a)`.

## Broadcasting

A veces es útil realizar operaciones binarias elemento por elemento en arreglos de diferentes tamaños, como sumar un vector a cada columna de una matriz. Una forma ineficiente de hacer esto sería replicar el vector al tamaño de la matriz:

```julia-repl
julia> a = rand(2, 1); A = rand(2, 3);

julia> repeat(a, 1, 3) + A
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846
```

Esto es derrochador cuando las dimensiones son grandes, así que Julia proporciona [`broadcast`](@ref), que expande las dimensiones singleton en los argumentos de matriz para que coincidan con la dimensión correspondiente en la otra matriz sin usar memoria extra, y aplica la función dada elemento por elemento:

```julia-repl
julia> broadcast(+, a, A)
2×3 Array{Float64,2}:
 1.20813  1.82068  1.25387
 1.56851  1.86401  1.67846

julia> b = rand(1,2)
1×2 Array{Float64,2}:
 0.867535  0.00457906

julia> broadcast(+, a, b)
2×2 Array{Float64,2}:
 1.71056  0.847604
 1.73659  0.873631
```

[Dotted operators](@ref man-dot-operators) como `.+` y `.*` son equivalentes a llamadas de `broadcast` (excepto que fusionan, como [described above](@ref man-array-and-vectorized-operators-and-functions)). También hay una función [`broadcast!`](@ref) para especificar un destino explícito (que también se puede acceder de manera de fusión mediante la asignación `.=`). De hecho, `f.(args...)` es equivalente a `broadcast(f, args...)`, proporcionando una sintaxis conveniente para transmitir cualquier función ([dot syntax](@ref man-vectorized)). Las "llamadas de punto" anidadas `f.(...)` (incluyendo llamadas a `.+` etcétera) [automatically fuse](@ref man-dot-operators) en una sola llamada de `broadcast`.

Además, [`broadcast`](@ref) no se limita a arreglos (ver la documentación de la función); también maneja escalares, tuplas y otras colecciones. Por defecto, solo algunos tipos de argumentos se consideran escalares, incluyendo (pero no limitado a) `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s y algunos singleton comunes como `missing` y `nothing`. Todos los demás argumentos se iteran o se indexan elemento por elemento.

```jldoctest
julia> convert.(Float32, [1, 2])
2-element Vector{Float32}:
 1.0
 2.0

julia> ceil.(UInt8, [1.2 3.4; 5.6 6.7])
2×2 Matrix{UInt8}:
 0x02  0x04
 0x06  0x07

julia> string.(1:3, ". ", ["First", "Second", "Third"])
3-element Vector{String}:
 "1. First"
 "2. Second"
 "3. Third"
```

A veces, deseas que un contenedor (como un arreglo) que normalmente participaría en la difusión esté "protegido" del comportamiento de difusión de iterar sobre todos sus elementos. Al colocarlo dentro de otro contenedor (como un único elemento [`Tuple`](@ref)), la difusión lo tratará como un único valor.

```jldoctest
julia> ([1, 2, 3], [4, 5, 6]) .+ ([1, 2, 3],)
([2, 4, 6], [5, 7, 9])

julia> ([1, 2, 3], [4, 5, 6]) .+ tuple([1, 2, 3])
([2, 4, 6], [5, 7, 9])
```

## Implementation

El tipo de arreglo base en Julia es el tipo abstracto [`AbstractArray{T,N}`](@ref). Está parametrizado por el número de dimensiones `N` y el tipo de elemento `T`. [`AbstractVector`](@ref) y [`AbstractMatrix`](@ref) son alias para los casos de 1-d y 2-d. Las operaciones en objetos `AbstractArray` se definen utilizando operadores y funciones de nivel superior, de una manera que es independiente del almacenamiento subyacente. Estas operaciones generalmente funcionan correctamente como una alternativa para cualquier implementación específica de arreglo.

El tipo `AbstractArray` incluye cualquier cosa vagamente similar a un arreglo, y las implementaciones de este pueden ser bastante diferentes de los arreglos convencionales. Por ejemplo, los elementos pueden ser calculados bajo demanda en lugar de estar almacenados. Sin embargo, cualquier tipo concreto `AbstractArray{T,N}` debería implementar generalmente al menos [`size(A)`](@ref) (devolviendo una tupla `Int`), [`getindex(A, i)`](@ref) y [`getindex(A, i1, ..., iN)`](@ref getindex); los arreglos mutables también deberían implementar [`setindex!`](@ref). Se recomienda que estas operaciones tengan una complejidad de tiempo casi constante, ya que de lo contrario algunas funciones de arreglo pueden ser inesperadamente lentas. Los tipos concretos también deberían proporcionar típicamente un método [`similar(A, T=eltype(A), dims=size(A))`](@ref), que se utiliza para asignar un arreglo similar para [`copy`](@ref) y otras operaciones fuera de lugar. No importa cómo se represente internamente un `AbstractArray{T,N}`, `T` es el tipo de objeto devuelto por la indexación *entera* (`A[1, ..., 1]`, cuando `A` no está vacío) y `N` debería ser la longitud de la tupla devuelta por [`size`](@ref). Para más detalles sobre cómo definir implementaciones personalizadas de `AbstractArray`, consulte el [array interface guide in the interfaces chapter](@ref man-interface-array).

`DenseArray` es un subtipo abstracto de `AbstractArray` destinado a incluir todos los arreglos donde los elementos se almacenan de manera contigua en orden de columna (ver [additional notes in Performance Tips](@ref man-performance-column-major)). El tipo [`Array`](@ref) es una instancia específica de `DenseArray`; [`Vector`](@ref) y [`Matrix`](@ref) son alias para los casos de 1-d y 2-d. Muy pocas operaciones están implementadas específicamente para `Array` más allá de aquellas que son requeridas para todos los `AbstractArray`; gran parte de la biblioteca de arreglos está implementada de manera genérica que permite que todos los arreglos personalizados se comporten de manera similar.

`SubArray` es una especialización de `AbstractArray` que realiza indexación compartiendo memoria con el array original en lugar de copiarlo. Un `SubArray` se crea con la función [`view`](@ref), que se llama de la misma manera que [`getindex`](@ref) (con un array y una serie de argumentos de índice). El resultado de `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` se ve igual que el resultado de `4d61726b646f776e2e436f64652822222c2022676574696e6465782229_40726566`, excepto que los datos se dejan en su lugar. `4d61726b646f776e2e436f64652822222c2022766965772229_40726566` almacena los vectores de índice de entrada en un objeto `SubArray`, que luego se puede usar para indexar el array original de manera indirecta. Al poner el macro [`@views`](@ref) delante de una expresión o bloque de código, cualquier rebanada `array[...]` en esa expresión se convertirá para crear una vista `SubArray`.

[`BitArray`](@ref) son arreglos booleanos "empaquetados" que son eficientes en espacio, los cuales almacenan un bit por valor booleano. Pueden ser utilizados de manera similar a los arreglos `Array{Bool}` (que almacenan un byte por valor booleano), y se pueden convertir de/a los últimos a través de `Array(bitarray)` y `BitArray(array)`, respectivamente.

Un arreglo es "estriado" si se almacena en memoria con espacios bien definidos (estrías) entre sus elementos. Un arreglo estriado con un tipo de elemento soportado puede ser pasado a una biblioteca externa (no Julia) como BLAS o LAPACK simplemente pasando su [`pointer`](@ref) y la estría para cada dimensión. El [`stride(A, d)`](@ref) es la distancia entre elementos a lo largo de la dimensión `d`. Por ejemplo, el `Array` incorporado devuelto por `rand(5,7,2)` tiene sus elementos dispuestos de manera contigua en orden mayor de columna. Esto significa que la estría de la primera dimensión — el espacio entre elementos en la misma columna — es `1`:

```julia-repl
julia> A = rand(5, 7, 2);

julia> stride(A, 1)
1
```

El paso de la segunda dimensión es el espacio entre elementos en la misma fila, saltando tantos elementos como hay en una sola columna (`5`). De manera similar, saltar entre las dos "páginas" (en la tercera dimensión) requiere saltar `5*7 == 35` elementos. El [`strides`](@ref) de este arreglo es la tupla de estos tres números juntos:

```julia-repl
julia> strides(A)
(1, 5, 35)
```

En este caso particular, el número de elementos omitidos *en memoria* coincide con el número de *índices lineales* omitidos. Esto solo es cierto para arreglos contiguos como `Array` (y otros subtipos de `DenseArray`) y no es cierto en general. Las vistas con índices de rango son un buen ejemplo de arreglos estratificados *no contiguos*; considera `V = @view A[1:3:4, 2:2:6, 2:-1:1]`. Esta vista `V` se refiere a la misma memoria que `A`, pero está omitiendo y reorganizando algunos de sus elementos. El paso de la primera dimensión de `V` es `3` porque solo estamos seleccionando cada tercera fila de nuestro arreglo original:

```julia-repl
julia> V = @view A[1:3:4, 2:2:6, 2:-1:1];

julia> stride(V, 1)
3
```

Esta vista selecciona de manera similar cada segunda columna de nuestro original `A` — y por lo tanto necesita omitir el equivalente a dos columnas de cinco elementos al moverse entre índices en la segunda dimensión:

```julia-repl
julia> stride(V, 2)
10
```

La tercera dimensión es interesante porque su orden está invertido. ¡Así que para pasar de la primera "página" a la segunda debe ir *hacia atrás* en la memoria, y por lo tanto su paso en esta dimensión es negativo!

```julia-repl
julia> stride(V, 3)
-35
```

Esto significa que el `puntero` para `V` está apuntando en realidad al medio del bloque de memoria de `A`, y se refiere a elementos tanto hacia atrás como hacia adelante en la memoria. Consulte el [interface guide for strided arrays](@ref man-interface-strided-arrays) para obtener más detalles sobre cómo definir sus propios arreglos estratificados. [`StridedVector`](@ref) y [`StridedMatrix`](@ref) son alias convenientes para muchos de los tipos de arreglos integrados que se consideran arreglos estratificados, lo que les permite despachar a implementaciones especializadas que llaman funciones BLAS y LAPACK altamente ajustadas y optimizadas utilizando solo el puntero y los pasos.

Es importante enfatizar que los pasos se refieren a desplazamientos en la memoria en lugar de indexación. Si estás buscando convertir entre indexación lineal (de un solo índice) e indexación cartesiana (de múltiples índices), consulta [`LinearIndices`](@ref) y [`CartesianIndices`](@ref).
