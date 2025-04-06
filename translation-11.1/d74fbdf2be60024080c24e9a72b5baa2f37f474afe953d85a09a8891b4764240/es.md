# SubArrays

El tipo `SubArray` de Julia es un contenedor que codifica una "vista" de un padre [`AbstractArray`](@ref). Esta página documenta algunos de los principios de diseño y la implementación de los `SubArray`.

Uno de los principales objetivos de diseño es garantizar un alto rendimiento para las vistas de ambos [`IndexLinear`](@ref) y [`IndexCartesian`](@ref) arreglos. Además, las vistas de los arreglos `IndexLinear` deberían ser ellas mismas `IndexLinear` en la medida de lo posible.

## Index replacement

Considera hacer rebanadas 2D de un arreglo 3D:

```@meta
DocTestSetup = :(import Random; Random.seed!(1234))
```

```jldoctest subarray
julia> A = rand(2,3,4);

julia> S1 = view(A, :, 1, 2:3)
2×2 view(::Array{Float64, 3}, :, 1, 2:3) with eltype Float64:
 0.839622  0.711389
 0.967143  0.103929

julia> S2 = view(A, 1, :, 2:3)
3×2 view(::Array{Float64, 3}, 1, :, 2:3) with eltype Float64:
 0.839622  0.711389
 0.789764  0.806704
 0.566704  0.962715
```

```@meta
DocTestSetup = nothing
```

`view` elimina las dimensiones "singleton" (las que se especifican con un `Int`), por lo que tanto `S1` como `S2` son `SubArray`s bidimensionales. En consecuencia, la forma natural de indexar estos es con `S1[i,j]`. Para extraer el valor del array padre `A`, el enfoque natural es reemplazar `S1[i,j]` con `A[i,1,(2:3)[j]]` y `S2[i,j]` con `A[1,i,(2:3)[j]]`.

La característica clave del diseño de SubArrays es que este reemplazo de índice se puede realizar sin ningún costo de tiempo de ejecución.

## SubArray design

### Type parameters and fields

La estrategia adoptada se expresa ante todo en la definición del tipo:

```julia
struct SubArray{T,N,P,I,L} <: AbstractArray{T,N}
    parent::P
    indices::I
    offset1::Int       # for linear indexing and pointer, only valid when L==true
    stride1::Int       # used only for linear indexing
    ...
end
```

`SubArray` tiene 5 parámetros de tipo. Los primeros dos son el tipo de elemento estándar y la dimensionalidad. El siguiente es el tipo del `AbstractArray` padre. El parámetro más utilizado es el cuarto, una `Tuple` de los tipos de los índices para cada dimensión. El último, `L`, se proporciona solo como una conveniencia para el despacho; es un booleano que representa si los tipos de índice admiten indexación lineal rápida. Más sobre eso más adelante.

Si en nuestro ejemplo anterior `A` es un `Array{Float64, 3}`, nuestro caso `S1` anterior sería un `SubArray{Float64,2,Array{Float64,3},Tuple{Base.Slice{Base.OneTo{Int64}},Int64,UnitRange{Int64}},false}`. Nota en particular el parámetro de tupla, que almacena los tipos de los índices utilizados para crear `S1`. Asimismo,

```jldoctest subarray
julia> S1.indices
(Base.Slice(Base.OneTo(2)), 1, 2:3)
```

Almacenar estos valores permite el reemplazo de índices, y tener los tipos codificados como parámetros permite despachar a algoritmos eficientes.

### Index translation

Realizar la traducción de índices requiere que se hagan diferentes cosas para diferentes tipos concretos de `SubArray`. Por ejemplo, para `S1`, se necesita aplicar los índices `i,j` a la primera y tercera dimensiones del array padre, mientras que para `S2` se deben aplicar a la segunda y tercera. El enfoque más simple para la indexación sería hacer el análisis de tipos en tiempo de ejecución:

```julia
parentindices = Vector{Any}()
for thisindex in S.indices
    ...
    if isa(thisindex, Int)
        # Don't consume one of the input indices
        push!(parentindices, thisindex)
    elseif isa(thisindex, AbstractVector)
        # Consume an input index
        push!(parentindices, thisindex[inputindex[j]])
        j += 1
    elseif isa(thisindex, AbstractMatrix)
        # Consume two input indices
        push!(parentindices, thisindex[inputindex[j], inputindex[j+1]])
        j += 2
    elseif ...
end
S.parent[parentindices...]
```

Desafortunadamente, esto sería desastroso en términos de rendimiento: cada acceso a un elemento asignaría memoria e implicaría la ejecución de mucho código mal tipado.

El mejor enfoque es despachar a métodos específicos para manejar cada tipo de índice almacenado. Eso es lo que hace `reindex`: despacha según el tipo del primer índice almacenado y consume el número apropiado de índices de entrada, y luego recursiona sobre los índices restantes. En el caso de `S1`, esto se expande a

```julia
Base.reindex(S1, S1.indices, (i, j)) == (i, S1.indices[2], S1.indices[3][j])
```

para cualquier par de índices `(i,j)` (excepto [`CartesianIndex`](@ref)s y arreglos de los mismos, ver más abajo).

Este es el núcleo de un `SubArray`; los métodos de indexación dependen de `reindex` para realizar esta traducción de índices. A veces, sin embargo, podemos evitar la indirecta y hacerlo aún más rápido.

### Linear indexing

La indexación lineal se puede implementar de manera eficiente cuando toda la matriz tiene un solo paso que separa los elementos sucesivos, comenzando desde algún desplazamiento. Esto significa que podemos pre-calcular estos valores y representar la indexación lineal simplemente como una suma y una multiplicación, evitando la indirecta de `reindex` y (más importante) la lenta computación de las coordenadas cartesianas por completo.

Para los tipos `SubArray`, la disponibilidad de indexación lineal eficiente se basa puramente en los tipos de los índices y no depende de valores como el tamaño del arreglo padre. Puedes preguntar si un conjunto dado de índices admite una indexación lineal rápida con la función interna `Base.viewindexing`:

```jldoctest subarray
julia> Base.viewindexing(S1.indices)
IndexCartesian()

julia> Base.viewindexing(S2.indices)
IndexLinear()
```

Esto se calcula durante la construcción del `SubArray` y se almacena en el parámetro de tipo `L` como un booleano que codifica el soporte de indexación lineal rápida. Aunque no es estrictamente necesario, significa que podemos definir el despacho directamente sobre `SubArray{T,N,A,I,true}` sin intermediarios.

Dado que este cálculo no depende de los valores en tiempo de ejecución, puede perder algunos casos en los que el paso resulta ser uniforme:

```jldoctest
julia> A = reshape(1:4*2, 4, 2)
4×2 reshape(::UnitRange{Int64}, 4, 2) with eltype Int64:
 1  5
 2  6
 3  7
 4  8

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 2
 2
```

Una vista construida como `view(A, 2:2:4, :)` tiene un paso uniforme, y por lo tanto, la indexación lineal podría realizarse de manera eficiente. Sin embargo, el éxito en este caso depende del tamaño del arreglo: si la primera dimensión fuera impar,

```jldoctest
julia> A = reshape(1:5*2, 5, 2)
5×2 reshape(::UnitRange{Int64}, 5, 2) with eltype Int64:
 1   6
 2   7
 3   8
 4   9
 5  10

julia> diff(A[2:2:4,:][:])
3-element Vector{Int64}:
 2
 3
 2
```

entonces `A[2:2:4,:]` no tiene un paso uniforme, por lo que no podemos garantizar un indexado lineal eficiente. Dado que tenemos que basar esta decisión únicamente en los tipos codificados en los parámetros del `SubArray`, `S = view(A, 2:2:4, :)` no puede implementar un indexado lineal eficiente.

### A few details

  * Tenga en cuenta que la función `Base.reindex` es agnóstica a los tipos de los índices de entrada; simplemente determina cómo y dónde deben ser reindexados los índices almacenados. No solo admite índices enteros, sino que también admite indexación no escalar. ¡Esto significa que las vistas de vistas no necesitan dos niveles de indireccionamiento; simplemente pueden volver a calcular los índices en el arreglo padre original!
  * Con suerte, para este momento está bastante claro que el soporte de cortes significa que la dimensionalidad, dada por el parámetro `N`, no es necesariamente igual a la dimensionalidad del array padre o la longitud de la tupla `indices`. Tampoco es necesario que los índices proporcionados por el usuario se alineen necesariamente con las entradas en la tupla `indices` (por ejemplo, el segundo índice proporcionado por el usuario podría corresponder a la tercera dimensión del array padre y el tercer elemento en la tupla `indices`).

    Lo que podría ser menos obvio es que la dimensionalidad del array padre almacenado debe ser igual al número de índices efectivos en la tupla `indices`. Algunos ejemplos:

    ```julia
    A = reshape(1:35, 5, 7) # A 2d parent Array
    S = view(A, 2:7)         # A 1d view created by linear indexing
    S = view(A, :, :, 1:1)   # Appending extra indices is supported
    ```

    Naivamente, pensarías que podrías simplemente establecer `S.parent = A` y `S.indices = (:,:,1:1)`, pero apoyar esto complica drásticamente el proceso de reindexación, especialmente para vistas de vistas. No solo necesitas despachar según los tipos de los índices almacenados, sino que también necesitas examinar si un índice dado es el final y "fusionar" cualquier índice almacenado restante. Esta no es una tarea fácil, y aún peor: es lenta ya que depende implícitamente de la indexación lineal.

    Afortunadamente, este es precisamente el cálculo que realiza `ReshapedArray`, y lo hace de manera lineal si es posible. En consecuencia, `view` asegura que el array padre tenga la dimensionalidad apropiada para los índices dados al reestructurarlo si es necesario. El constructor interno `SubArray` asegura que esta invariante se cumpla.
  * [`CartesianIndex`](@ref) y arreglos de este tipo lanzan una mala sorpresa en el esquema de `reindex`. Recuerda que `reindex` simplemente despacha según el tipo de los índices almacenados para determinar cuántos índices pasados deben ser utilizados y dónde deben ir. Pero con `CartesianIndex`, ya no hay una correspondencia uno a uno entre el número de argumentos pasados y el número de dimensiones en las que indexan. Si regresamos al ejemplo anterior de `Base.reindex(S1, S1.indices, (i, j))`, puedes ver que la expansión es incorrecta para `i, j = CartesianIndex(), CartesianIndex(2,1)`. Debería *saltar* el `CartesianIndex()` por completo y devolver:

    ```julia
    (CartesianIndex(2,1)[1], S1.indices[2], S1.indices[3][CartesianIndex(2,1)[2]])
    ```

    En su lugar, sin embargo, obtenemos:

    ```julia
    (CartesianIndex(), S1.indices[2], S1.indices[3][CartesianIndex(2,1)])
    ```

    Hacer esto correctamente requeriría un despacho *combinado* en ambos índices almacenados y pasados a través de todas las combinaciones de dimensionalidades de una manera intratable. Como tal, `reindex` nunca debe ser llamado con índices de `CartesianIndex`. Afortunadamente, el caso escalar se maneja fácilmente al aplanar primero los argumentos de `CartesianIndex` a enteros simples. Sin embargo, los arreglos de `CartesianIndex` no pueden ser separados en piezas ortogonales tan fácilmente. Antes de intentar usar `reindex`, `view` debe asegurarse de que no haya arreglos de `CartesianIndex` en la lista de argumentos. Si los hay, puede simplemente "dejarlo pasar" evitando el cálculo de `reindex` por completo, construyendo un `SubArray` anidado con dos niveles de indirecta en su lugar.
