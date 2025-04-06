```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

초기화되지 않은 `N`-차원 [`Array`](@ref)를 생성하여 타입 `T`의 요소를 포함합니다. `N`은 `Array{T,N}(undef, dims)`와 같이 명시적으로 제공되거나 `dims`의 길이나 개수에 의해 결정될 수 있습니다. `dims`는 각 차원의 길이에 해당하는 정수 인수의 튜플 또는 시리즈일 수 있습니다. 랭크 `N`이 명시적으로 제공되면, `dims`의 길이나 개수와 일치해야 합니다. 여기서 [`undef`](@ref)는 [`UndefInitializer`](@ref)입니다.

# 예제

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N이 명시적으로 주어짐
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N이 입력에 의해 결정됨
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # typeof(B)와 주어진 크기를 사용
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
