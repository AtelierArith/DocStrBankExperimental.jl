```
size(A::AbstractArray, [dim])
```

`A`의 차원을 포함하는 튜플을 반환합니다. 선택적으로 특정 차원을 지정하여 해당 차원의 길이만 가져올 수 있습니다.

`size`는 비표준 인덱스를 가진 배열에 대해 정의되지 않을 수 있으며, 이 경우 [`axes`](@ref)가 유용할 수 있습니다. [사용자 정의 인덱스를 가진 배열](@ref man-custom-indices)에 대한 매뉴얼 장을 참조하십시오.

또한: [`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref).

# 예제

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
