```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

벡터 `v`의 부분 순열 `I`를 반환하여, `v[I]`가 인덱스 `k`에서 `v`의 완전히 정렬된 버전의 값을 반환하도록 합니다. `k`가 범위인 경우 인덱스의 벡터가 반환되고, `k`가 정수인 경우 단일 인덱스가 반환됩니다. 순서는 `sort!`와 동일한 키워드를 사용하여 지정됩니다. 이 순열은 안정적이며, 동일한 요소의 인덱스는 오름차순으로 나타납니다.

이 함수는 `sortperm(...)[k]`를 호출하는 것과 동등하지만, 더 효율적입니다.

# 예제

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```
