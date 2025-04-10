```
mod1(x, y)
```

바닥 나눗셈 후의 모듈로, 양수 `y`에 대해 범위 $(0, y]$에서 `mod(r, y) == mod(x, y)`가 성립하는 값 `r`을 반환하고, 음수 `y`에 대해 범위 $[y,0)$에서 성립합니다.

정수 인수와 양수 `y`에 대해, 이는 `mod(x, 1:y)`와 같으며, 따라서 1 기반 인덱싱에 자연스럽습니다. 반면에, `mod(x, y) == mod(x, 0:y-1)`는 오프셋이나 보폭을 가진 계산에 자연스럽습니다.

자세한 내용은 [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
