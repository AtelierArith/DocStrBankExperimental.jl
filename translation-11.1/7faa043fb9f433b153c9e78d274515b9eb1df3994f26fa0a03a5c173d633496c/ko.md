```
Iterators.accumulate(f, itr; [init])
```

2개의 인자를 가지는 함수 `f`와 반복자 `itr`가 주어지면, 이전 값과 `itr`의 다음 요소에 `f`를 차례로 적용하는 새로운 반복자를 반환합니다.

이는 사실상 [`Base.accumulate`](@ref)의 지연 버전입니다.

!!! compat "Julia 1.5"
    키워드 인자 `init`은 Julia 1.5에서 추가되었습니다.


# 예제

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
