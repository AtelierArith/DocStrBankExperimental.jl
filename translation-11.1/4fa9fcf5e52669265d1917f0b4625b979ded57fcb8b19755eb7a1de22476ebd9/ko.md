# Collections and Data Structures

## [Iteration](@id lib-collections-iteration)

순차 반복은 [`iterate`](@ref) 함수에 의해 구현됩니다. 일반적인 `for` 루프:

```julia
for i in iter   # or  "for i = iter"
    # body
end
```

is translated into:

```julia
next = iterate(iter)
while next !== nothing
    (i, state) = next
    # body
    next = iterate(iter, state)
end
```

`state` 객체는 무엇이든 될 수 있으며, 각 반복 가능한 유형에 적합하게 선택해야 합니다. 사용자 정의 반복 가능한 유형을 정의하는 방법에 대한 자세한 내용은 [manual section on the iteration interface](@ref man-interface-iteration)을 참조하세요.

```@docs
Base.iterate
Base.IteratorSize
Base.IteratorEltype
```

완전히 구현됨:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`Number`](@ref)
  * [`AbstractArray`](@ref)
  * [`BitSet`](@ref)
  * [`IdDict`](@ref)
  * [`Dict`](@ref)
  * [`WeakKeyDict`](@ref)
  * `각줄`
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

완전히 구현됨:

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

완전히 구현됨:

  * [`Array`](@ref)
  * [`BitArray`](@ref)
  * [`AbstractArray`](@ref)
  * `서브배열`

부분적으로 구현됨:

  * [`AbstractRange`](@ref)
  * [`UnitRange`](@ref)
  * [`Tuple`](@ref)
  * [`AbstractString`](@ref)
  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)
  * [`NamedTuple`](@ref)

## Dictionaries

[`Dict`](@ref)는 표준 사전입니다. 그 구현은 키에 대한 해싱 함수로 [`hash`](@ref)를 사용하고, 동등성을 결정하기 위해 [`isequal`](@ref)를 사용합니다. 사용자 정의 유형에 대해 이 두 함수를 정의하여 해시 테이블에 저장되는 방식을 재정의하십시오.

[`IdDict`](@ref)는 키가 항상 객체 식별자인 특별한 해시 테이블입니다.

[`WeakKeyDict`](@ref)는 키가 객체에 대한 약한 참조인 해시 테이블 구현으로, 해시 테이블에서 참조되고 있더라도 가비지 컬렉션될 수 있습니다. `Dict`와 마찬가지로 해싱을 위해 `hash`를 사용하고 동등성을 위해 `isequal`을 사용하지만, `Dict`와는 달리 삽입 시 키를 변환하지 않습니다.

[`Dict`](@ref)는 `=>`로 구성된 쌍 객체를 `4d61726b646f776e2e436f64652822222c2022446963742229_40726566` 생성자에 전달하여 생성할 수 있습니다: `Dict("A"=>1, "B"=>2)`. 이 호출은 키와 값에서 타입 정보를 유추하려고 시도합니다 (즉, 이 예제는 `Dict{String, Int64}`를 생성합니다). 타입을 명시적으로 지정하려면 `Dict{KeyType,ValueType}(...)` 구문을 사용하세요. 예를 들어, `Dict{String,Int32}("A"=>1, "B"=>2)`입니다.

사전은 생성기를 사용하여 생성할 수도 있습니다. 예를 들어, `Dict(i => f(i) for i = 1:10)`입니다.

주어진 사전 `D`에서 구문 `D[x]`는 키 `x`의 값을 반환합니다(존재하는 경우) 또는 오류를 발생시키며, `D[x] = y`는 키-값 쌍 `x => y`를 `D`에 저장합니다(키 `x`에 대한 기존 값을 대체함). `D[...]`에 대한 여러 인수는 튜플로 변환됩니다. 예를 들어, 구문 `D[x,y]`는 `D[(x,y)]`와 동일하며, 즉 튜플 `(x,y)`로 키가 지정된 값을 참조합니다.

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

완전히 구현됨:

  * [`Dict`](@ref)
  * [`IdDict`](@ref)
  * [`WeakKeyDict`](@ref)

부분적으로 구현됨:

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

완전히 구현됨:

  * [`Set`](@ref)
  * [`BitSet`](@ref)
  * [`IdSet`](@ref)

부분적으로 구현됨:

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

완전히 구현됨:

  * `벡터` (즉, 1차원 [`Array`](@ref))
  * `BitVector` (일명 1차원 [`BitArray`](@ref))

## Utility Collections

```@docs
Base.Pair
Iterators.Pairs
```
