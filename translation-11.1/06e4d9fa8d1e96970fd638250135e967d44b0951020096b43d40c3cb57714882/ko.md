```
string(xs...)
```

어떤 값으로부터 문자열을 생성하려면 [`print`](@ref) 함수를 사용하세요.

`string`은 일반적으로 직접 정의하지 않아야 합니다. 대신, `print(io::IO, x::MyType)` 메서드를 정의하세요. 특정 타입에 대해 `string(x)`가 매우 효율적이어야 하는 경우, `string`에 메서드를 추가하고 `print(io::IO, x::MyType) = print(io, string(x))`를 정의하여 함수들이 일관성을 유지하도록 하는 것이 좋습니다.

또한 참고하세요: [`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show).

# 예제

```jldoctest
julia> string("a", 1, true)
"a1true"
```
