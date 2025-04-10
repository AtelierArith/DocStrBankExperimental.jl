```
>>>(x, n)
```

부호 없는 오른쪽 비트 시프트 연산자, `x >>> n`. `n >= 0`인 경우, 결과는 `x`를 `n` 비트만큼 오른쪽으로 시프트하고 `0`으로 채웁니다. `n < 0`인 경우, 이는 `x << -n`과 같습니다.

[`Unsigned`](@ref) 정수 타입의 경우, 이는 [`>>`](@ref)와 같습니다. [`Signed`](@ref) 정수 타입의 경우, 이는 `signed(unsigned(x) >> n)`과 같습니다.

# 예제

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

[`BigInt`](@ref)는 무한 크기를 가진 것으로 간주되므로 채우기가 필요 없으며 이는 [`>>`](@ref)와 같습니다.

또한 [`>>`](@ref), [`<<`](@ref)를 참조하세요.
