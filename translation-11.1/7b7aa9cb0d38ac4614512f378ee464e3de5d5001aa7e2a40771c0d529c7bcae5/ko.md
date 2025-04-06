```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

`y::T`를 찾아라. 여기서 `x` ≡ `y` (mod n)이며, n은 `T`에서 표현 가능한 정수의 수이고, `y`는 `[typemin(T),typemax(T)]` 범위의 정수이다. 만약 `T`가 모든 정수를 표현할 수 있다면 (예: `T == BigInt`), 이 연산은 `T`로의 변환에 해당한다.

# 예제

```jldoctest
julia> x = 129 % Int8
-127

julia> typeof(x)
Int8

julia> x = 129 % BigInt
129

julia> typeof(x)
BigInt
```
