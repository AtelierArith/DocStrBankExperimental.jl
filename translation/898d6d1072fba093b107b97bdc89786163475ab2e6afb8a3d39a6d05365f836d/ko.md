```
repeated(x[, n::Int])
```

값 `x`를 영원히 생성하는 반복자입니다. `n`이 지정되면, `x`를 그만큼 생성합니다 (이는 `take(repeated(x), n)`과 동일합니다).

또한 [`fill`](@ref Base.fill)과 [`Iterators.cycle`](@ref)와 비교하십시오.

# 예제

```jldoctest
julia> a = Iterators.repeated([1 2], 4);

julia> collect(a)
4-element Vector{Matrix{Int64}}:
 [1 2]
 [1 2]
 [1 2]
 [1 2]

julia> ans == fill([1 2], 4)
true

julia> Iterators.cycle([1 2], 4) |> collect |> println
[1, 2, 1, 2, 1, 2, 1, 2]
```
