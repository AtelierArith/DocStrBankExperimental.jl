```
Iterators.filter(flt, itr)
```

주어진 술어 함수 `flt`와 반복 가능한 객체 `itr`에 대해, `flt(x)`를 만족하는 `itr`의 요소 `x`를 반복할 때 생성하는 반복 가능한 객체를 반환합니다. 원래 반복자의 순서는 유지됩니다.

이 함수는 *지연* 방식입니다; 즉, $Θ(1)$ 시간에 반환되고 $Θ(1)$의 추가 공간을 사용하며, `filter`의 호출로 `flt`가 호출되지 않을 것임이 보장됩니다. 반환된 반복 가능한 객체를 반복할 때 `flt`에 대한 호출이 이루어집니다. 이러한 호출은 캐시되지 않으며, 반복할 때마다 반복 호출이 이루어집니다.

!!! 경고     `filter`에서 반환된 반복자에 대한 후속 *지연* 변환, 예를 들어 `Iterators.reverse`나 `cycle`에 의해 수행되는 변환은 반환된 반복 가능한 객체를 수집하거나 반복할 때까지 `flt`에 대한 호출을 지연시킵니다. 필터 술어가 비결정적이거나 반환 값이 `itr`의 요소에 대한 반복 순서에 따라 달라지는 경우, 지연 변환과의 조합은 놀라운 동작을 초래할 수 있습니다. 이것이 바람직하지 않다면, `flt`가 순수 함수인지 확인하거나 추가 변환 전에 중간 `filter` 반복자를 수집하십시오.

배열에 대한 필터링의 즉각적인 구현에 대해서는 [`Base.filter`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # Iterators.filter를 통해 생성기를 수집합니다.
3-element Vector{Int64}:
 1
 3
 5
```
