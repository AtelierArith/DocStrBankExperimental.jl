```
randsubseq!([rng=default_rng(),] S, A, p)
```

[`randsubseq`](@ref)와 유사하지만, 결과는 `S`에 저장됩니다(필요에 따라 크기가 조정됨).

# 예제

```jldoctest
julia> S = Int64[];

julia> randsubseq!(Xoshiro(123), S, 1:8, 0.3)
2-element Vector{Int64}:
 4
 7

julia> S
2-element Vector{Int64}:
 4
 7
```
