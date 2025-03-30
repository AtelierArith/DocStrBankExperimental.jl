```
digits!(array, n::Integer; base::Integer = 10)
```

주어진 진수에서 `n`의 자릿수를 배열에 채웁니다. 더 중요한 자릿수는 더 높은 인덱스에 위치합니다. 배열 길이가 부족하면 가장 덜 중요한 자릿수로 배열 길이까지 채워집니다. 배열 길이가 과도하면 초과 부분은 0으로 채워집니다.

# 예제

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
