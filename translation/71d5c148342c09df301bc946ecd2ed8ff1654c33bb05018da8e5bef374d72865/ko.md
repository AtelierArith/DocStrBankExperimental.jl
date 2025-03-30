```
unique(f, itr)
```

`itr`의 요소에 적용된 `f`에 의해 생성된 각 고유 값에 대해 `itr`에서 하나의 값을 포함하는 배열을 반환합니다.

# 예제

```jldoctest
julia> unique(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4
```

이 기능은 배열에서 고유 요소의 첫 번째 발생의 *인덱스*를 추출하는 데에도 사용할 수 있습니다:

```jldoctest
julia> a = [3.1, 4.2, 5.3, 3.1, 3.1, 3.1, 4.2, 1.7];

julia> i = unique(i -> a[i], eachindex(a))
4-element Vector{Int64}:
 1
 2
 3
 8

julia> a[i]
4-element Vector{Float64}:
 3.1
 4.2
 5.3
 1.7

julia> a[i] == unique(a)
true
```
