```
fill!(A, x)
```

배열 `A`를 값 `x`로 채웁니다. `x`가 객체 참조인 경우, 모든 요소는 동일한 객체를 참조합니다. `fill!(A, Foo())`는 `Foo()`를 한 번 평가한 결과로 채워진 `A`를 반환합니다.

# 예제

```jldoctest
julia> A = zeros(2,3)
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2.)
2×3 Matrix{Float64}:
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> a = [1, 1, 1]; A = fill!(Vector{Vector{Int}}(undef, 3), a); a[1] = 2; A
3-element Vector{Vector{Int64}}:
 [2, 1, 1]
 [2, 1, 1]
 [2, 1, 1]

julia> x = 0; f() = (global x += 1; x); fill!(Vector{Int}(undef, 3), f())
3-element Vector{Int64}:
 1
 1
 1
```
