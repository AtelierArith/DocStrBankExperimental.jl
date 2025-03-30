```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

벡터 `v`를 제자리에서 부분 정렬하여 인덱스 `k`(또는 `k`가 범위인 경우 인접한 값의 범위)에 있는 값이 배열이 완전히 정렬되었을 때 나타날 위치에 오도록 합니다. `k`가 단일 인덱스인 경우 해당 값이 반환되고, `k`가 범위인 경우 해당 인덱스의 값 배열이 반환됩니다. `partialsort!`는 입력 배열을 완전히 정렬하지 않을 수 있습니다.

키워드 인수에 대한 내용은 [`sort!`](@ref) 문서를 참조하세요.

# 예제

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
