```
Bool <: Integer
```

부울 타입, 값 `true`와 `false`를 포함합니다.

`Bool`은 일종의 숫자입니다: `false`는 수치적으로 `0`과 같고 `true`는 수치적으로 `1`과 같습니다. 게다가, `false`는 [`NaN`](@ref) 및 [`Inf`](@ref)에 대해 곱셈의 "강한 제로"로 작용합니다:

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

[`if`](@ref) 및 기타 조건문을 통해 분기할 때는 오직 `Bool`만 허용됩니다. Julia에는 "진리값"이 없습니다.

비교는 일반적으로 `Bool`을 반환하며, 브로드캐스트된 비교는 `Array{Bool}` 대신 [`BitArray`](@ref)를 반환할 수 있습니다.

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

자세한 내용은 [`trues`](@ref), [`falses`](@ref), [`ifelse`](@ref)를 참조하세요.
