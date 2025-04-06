```
Iterators.reverse(itr)
```

주어진 반복자 `itr`에 대해, `reverse(itr)`는 동일한 컬렉션에 대한 반복자이지만 역순으로 되어 있습니다. 이 반복자는 "지연(lazy)" 방식으로 작동하여 컬렉션을 복사하지 않고 역순으로 만듭니다; 즉, 열심히 구현된 [`Base.reverse`](@ref)를 참조하십시오.

(기본적으로, 이것은 `itr`을 감싸는 `Iterators.Reverse` 객체를 반환하며, 해당 [`iterate`](@ref) 메서드가 정의되어 있으면 반복할 수 있지만, 일부 `itr` 유형은 더 특수화된 `Iterators.reverse` 동작을 구현할 수 있습니다.)

모든 반복자 유형 `T`가 역순 반복을 지원하는 것은 아닙니다. 만약 `T`가 지원하지 않는다면, `Iterators.reverse(itr::T)`를 반복하면 [`MethodError`](@ref)가 발생합니다. 이는 `Iterators.Reverse{T}`에 대한 `iterate` 메서드가 누락되었기 때문입니다. (이 메서드를 구현하기 위해, 원래 반복자 `itr::T`는 `r::Iterators.Reverse{T}` 객체에서 `r.itr`로 얻을 수 있습니다; 더 일반적으로, `Iterators.reverse(r)`를 사용할 수 있습니다.)

# 예제

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
