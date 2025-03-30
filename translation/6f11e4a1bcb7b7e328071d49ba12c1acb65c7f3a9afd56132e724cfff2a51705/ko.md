```
NaN, NaN64
```

[`Float64`](@ref) 유형의 not-a-number 값입니다.

참고: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# 예제

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! note
    항상 `NaN`을 확인할 때는 [`isnan`](@ref) 또는 [`isequal`](@ref)를 사용하세요. `x === NaN`을 사용하면 예기치 않은 결과가 나올 수 있습니다:

    ```julia-repl
    julia> reinterpret(UInt32, NaN32)
    0x7fc00000

    julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
    NaN32

    julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
    (false, true, true)
    ```

