```
map!(function, destination, collection...)
```

[`map`](@ref)와 유사하지만, 새로운 컬렉션이 아닌 `destination`에 결과를 저장합니다. `destination`은 가장 작은 컬렉션만큼은 크기가 커야 합니다.

!!! warning
    변형된 인수 중 하나가 다른 인수와 메모리를 공유할 경우 예상치 못한 동작이 발생할 수 있습니다.


참고: [`map`](@ref), [`foreach`](@ref), [`zip`](@ref), [`copyto!`](@ref).

# 예제

```jldoctest
julia> a = zeros(3);

julia> map!(x -> x * 2, a, [1, 2, 3]);

julia> a
3-element Vector{Float64}:
 2.0
 4.0
 6.0

julia> map!(+, zeros(Int, 5), 100:999, 1:3)
5-element Vector{Int64}:
 101
 103
 105
   0
   0
```
