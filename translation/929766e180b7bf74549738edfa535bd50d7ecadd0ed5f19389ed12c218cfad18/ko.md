```
copyto!(dest::AbstractArray, src) -> dest
```

컬렉션 `src`의 모든 요소를 배열 `dest`로 복사합니다. `dest`의 길이는 `src`의 길이 `n`보다 크거나 같아야 합니다. `dest`의 첫 번째 `n` 요소는 덮어쓰여지며, 나머지 요소는 그대로 유지됩니다.

자세한 내용은 [`copy!`](@ref Base.copy!), [`copy`](@ref)를 참조하세요.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 예상치 못한 동작이 발생할 수 있습니다.

# 예제

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
