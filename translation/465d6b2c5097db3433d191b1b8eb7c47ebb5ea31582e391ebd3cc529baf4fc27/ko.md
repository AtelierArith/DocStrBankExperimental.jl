```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)`는 `x`의 절대값보다 작거나 같은 같은 유형의 가장 가까운 정수 값을 반환합니다.

`trunc(T, x)`는 결과를 유형 `T`로 변환하며, 잘린 값이 `T`로 표현할 수 없는 경우 `InexactError`를 발생시킵니다.

키워드 `digits`, `sigdigits` 및 `base`는 [`round`](@ref)와 동일하게 작동합니다.

새로운 유형에 대해 `trunc`를 지원하려면 `Base.round(x::NewType, ::RoundingMode{:ToZero})`를 정의하십시오.

참고: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# 예제

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
