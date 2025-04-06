```
issuccess(F::Factorization)
```

행렬의 인수가 성공적으로 이루어졌는지 테스트합니다.

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)`는 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
