```
issuccess(F::LU; allowsingular = false)
```

행렬의 LU 분해가 성공했는지 테스트합니다. 기본적으로 유효하지만 랭크가 부족한 U 인자를 생성하는 분해는 실패로 간주됩니다. `allowsingular = true`를 전달하여 이를 변경할 수 있습니다.

!!! compat "Julia 1.11"
    `allowsingular` 키워드 인자는 Julia 1.11에서 추가되었습니다.


# 예제

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
