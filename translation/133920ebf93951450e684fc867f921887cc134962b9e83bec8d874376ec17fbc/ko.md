```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

`A`에서 길이 `length(A)`의 무작위 순열을 생성합니다. 선택적 `rng` 인자는 난수 생성기를 지정합니다(자세한 내용은 [Random Numbers](@ref) 참조). 임의의 벡터를 무작위로 섞으려면 [`shuffle`](@ref) 또는 [`shuffle!`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
