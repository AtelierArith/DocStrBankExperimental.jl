```
ispow2(n::Number) -> Bool
```

`n`이 정수 형태의 2의 거듭제곱인지 테스트합니다.

자세한 내용은 [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    비-`Integer` 인자에 대한 지원은 Julia 1.6에서 추가되었습니다.

