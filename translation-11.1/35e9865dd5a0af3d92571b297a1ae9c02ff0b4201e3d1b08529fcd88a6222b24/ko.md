```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

정렬 함수가 부분 퀵 정렬 알고리즘을 사용해야 함을 나타냅니다. `PartialQuickSort(k)`는 `QuickSort`와 같지만, `v`가 완전히 정렬되었을 때 `v[k]`에 위치할 요소만 찾아서 정렬하는 데 필요합니다.

특징:

  * *안정적이지 않음*: 동등하게 비교되는 요소의 순서를 보존하지 않습니다 (예: 대소문자를 무시하는 문자 정렬에서 "a"와 "A").
  * *제자리*에서 메모리 내에서 수행됩니다.
  * *분할 정복*: [`MergeSort`](@ref)와 유사한 정렬 전략입니다.

`PartialQuickSort(k)`는 전체 배열을 반드시 정렬하지는 않습니다. 예를 들어,

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```
