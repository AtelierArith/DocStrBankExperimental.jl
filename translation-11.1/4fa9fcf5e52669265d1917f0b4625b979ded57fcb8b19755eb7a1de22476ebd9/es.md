# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

La iteración secuencial se implementa mediante la función [`iterate`](@ref). El bucle `for` general:

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

es se traduce como:

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

El objeto `state` puede ser cualquier cosa y debe ser elegido apropiadamente para cada tipo iterable. Consulte el [manual section on the iteration interface](@ref man-interface-iteration) para obtener más detalles sobre cómo definir un tipo iterable personalizado.

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

Totalmente implementado por:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `CadaLínea`
  * [`AbstractString`](@ref)
  * [`Set`](@ref)
  * [`Pair`](@ref)
  * [`NamedTuple`](@ref)

## Constructors and Types

```@docs
Base.AbstractRange
Base.OrdinalRange
Base.AbstractUnitRange
Base.StepRange
Base.UnitRange
Base.LinRange
```

## General Collections

```@docs
Base.isempty
Base.isdone
Base.empty!
Base.length
Base.checked_length
```

Totalmente implementado por:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`AbstractString`](@ref)
  * [`Set`](@ref)
  * [`NamedTuple`](@ref)

## Iterable Collections

```@docs
Base.in
Base.:∉
Base.hasfastin
Base.eltype
Base.indexin
Base.unique
Base.unique!
Base.allunique
Base.allequal
Base.reduce(::Any, ::Any)
Base.reduce(::Any, ::AbstractArray)
Base.foldl(::Any, ::Any)
Base.foldr(::Any, ::Any)
Base.maximum
Base.maximum!
Base.minimum
Base.minimum!
Base.extrema
Base.extrema!
Base.argmax
Base.argmin
Base.findmax
Base.findmin
Base.findmax!
Base.findmin!
Base.sum
Base.sum!
Base.prod
Base.prod!
Base.any(::Any)
Base.any(::AbstractArray, ::Any)
Base.any!
Base.all(::Any)
Base.all(::AbstractArray, ::Any)
Base.all!
Base.count
Base.foreach
Base.map
Base.map!
Base.mapreduce(::Any, ::Any, ::Any)
Base.mapfoldl(::Any, ::Any, ::Any)
Base.mapfoldr(::Any, ::Any, ::Any)
Base.first
Base.last
Base.front
Base.tail
Base.step
Base.collect(::Any)
Base.collect(::Type, ::Any)
Base.filter
Base.filter!
Base.replace(::Any, ::Pair...)
Base.replace(::Base.Callable, ::Any)
Base.replace!
Base.rest
Base.split_rest
```

## Indexable Collections

```@docs
Base.getindex
Base.setindex!
Base.firstindex
Base.lastindex
```

Totalmente implementado por:

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `SubArray`

Implementado parcialmente por:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref) es el diccionario estándar. Su implementación utiliza [`hash`](@ref) como la función de hash para la clave, y [`isequal`](@ref) para determinar la igualdad. Define estas dos funciones para tipos personalizados para anular cómo se almacenan en una tabla hash.

[`IdDict`](@ref) es una tabla hash especial donde las claves son siempre identidades de objetos.

[`WeakKeyDict`](@ref) es una implementación de tabla hash donde las claves son referencias débiles a objetos, y por lo tanto pueden ser recolectadas por el recolector de basura incluso cuando están referenciadas en una tabla hash. Al igual que `Dict`, utiliza `hash` para el hashing y `isequal` para la igualdad; a diferencia de `Dict`, no convierte las claves al insertarlas.

[`Dict`](@ref) se puede crear pasando objetos de par construidos con `=>` a un constructor de `4d61726b646f776e2e436f64652822222c2022446963742229_40726566`: `Dict("A"=>1, "B"=>2)`. Esta llamada intentará inferir información de tipo de las claves y valores (es decir, este ejemplo crea un `Dict{String, Int64}`). Para especificar tipos explícitamente, utiliza la sintaxis `Dict{KeyType,ValueType}(...)`. Por ejemplo, `Dict{String,Int32}("A"=>1, "B"=>2)`.

Los diccionarios también se pueden crear con generadores. Por ejemplo, `Dict(i => f(i) for i = 1:10)`.

Dado un diccionario `D`, la sintaxis `D[x]` devuelve el valor de la clave `x` (si existe) o lanza un error, y `D[x] = y` almacena el par clave-valor `x => y` en `D` (reemplazando cualquier valor existente para la clave `x`). Múltiples argumentos para `D[...]` se convierten en tuplas; por ejemplo, la sintaxis `D[x,y]` es equivalente a `D[(x,y)]`, es decir, se refiere al valor clave por la tupla `(x,y)`.

```@docs
Base.AbstractDict
Base.Dict
Base.IdDict
Base.WeakKeyDict
Base.ImmutableDict
Base.PersistentDict
Base.haskey
Base.get
Base.get!
Base.getkey
Base.delete!
Base.pop!(::Any, ::Any, ::Any)
Base.keys
Base.values
Base.pairs
Base.merge
Base.mergewith
Base.merge!
Base.mergewith!
Base.sizehint!
Base.keytype
Base.valtype
```

Totalmente implementado por:

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

Implementado parcialmente por:

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)
  * [`EnvDict`](@ref Base.EnvDict)
  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`ImmutableDict`](@ref Base.ImmutableDict)
  * [`PersistentDict`](@ref Base.PersistentDict)
  * [`Iterators.Pairs`](@ref)

## Set-Like Collections

```@docs
Base.AbstractSet
Base.Set
Base.BitSet
Base.IdSet
Base.union
Base.union!
Base.intersect
Base.setdiff
Base.setdiff!
Base.symdiff
Base.symdiff!
Base.intersect!
Base.issubset
Base.in!
Base.:⊈
Base.:⊊
Base.issetequal
Base.isdisjoint
```

Totalmente implementado por:

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

Implementado parcialmente por:

  * [`Array`](@ref)

## Dequeues

```@docs
Base.push!
Base.pop!
Base.popat!
Base.pushfirst!
Base.popfirst!
Base.insert!
Base.deleteat!
Base.keepat!
Base.splice!
Base.resize!
Base.append!
Base.prepend!
```

Totalmente implementado por:

  * `Vector` (también conocido como [`Array`](@ref))
  * `BitVector` (también conocido como [`BitArray`](@ref))

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
