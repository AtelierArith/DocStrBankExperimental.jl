```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

Adjoint/Transpose로 감싸진 벡터의 경우, `A`의 연산자 $q$-노름을 반환하며, 이는 `p`-노름과 동등하며 값은 `p = q/(q-1)`입니다. 이들은 `p = q = 2`에서 일치합니다. [`norm`](@ref)를 사용하여 벡터로서 `A`의 `p` 노름을 계산합니다.

벡터 공간과 그 쌍대 사이의 노름 차이는 쌍대성과 내적 간의 관계를 보존하기 위해 발생하며, 결과는 `1 × n` 행렬의 연산자 `p`-노름과 일치합니다.

# 예제

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
