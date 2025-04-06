```
mapslices(f, A; dims)
```

주어진 배열 `A`의 차원을 변환하여 각 슬라이스 `A[..., :, ..., :, ...]`에 함수 `f`를 적용합니다. 여기서 `dims`의 각 `d`에 콜론이 있습니다. 결과는 나머지 차원을 따라 연결됩니다.

예를 들어, `dims = [1,2]`이고 `A`가 4차원인 경우, `f`는 모든 `i`와 `j`에 대해 `x = A[:,:,i,j]`에서 호출되며, `f(x)`는 결과 `R`에서 `R[:,:,i,j]`가 됩니다.

또한 [`eachcol`](@ref) 또는 [`eachslice`](@ref)를 참조하십시오. 이는 [`map`](@ref) 또는 [`stack`](@ref)와 함께 사용됩니다.

# 예제

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) with eltype Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # 1×4 행렬을 반환합니다.

julia> B = mapslices(f, A, dims=(1,2))
1×4×3 Array{Int64, 3}:
[:, :, 1] =
 1  1  1  1

[:, :, 2] =
 11  11  11  11

[:, :, 3] =
 21  21  21  21

julia> f2(x::AbstractMatrix) = fill(x[1,1], 1,4);

julia> B == stack(f2, eachslice(A, dims=3))
true

julia> g(x) = x[begin] // x[end-1];  # 숫자를 반환합니다.

julia> mapslices(g, A, dims=[1,3])
1×5×1 Array{Rational{Int64}, 3}:
[:, :, 1] =
 1//21  3//23  1//5  7//27  9//29

julia> map(g, eachslice(A, dims=2))
5-element Vector{Rational{Int64}}:
 1//21
 3//23
 1//5
 7//27
 9//29

julia> mapslices(sum, A; dims=(1,3)) == sum(A; dims=(1,3))
true
```

`eachslice(A; dims=2)`에서 지정된 차원은 슬라이스에서 콜론이 없는 차원입니다. 이는 `view(A,:,i,:)`인 반면, `mapslices(f, A; dims=(1,3))`는 `A[:,i,:]`를 사용합니다. 함수 `f`는 `A`에 영향을 주지 않고 슬라이스의 값을 변경할 수 있습니다.
