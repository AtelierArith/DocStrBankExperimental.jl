```
floor([T,] x)
floor(x; digits::Integer= [, base = 10])
floor(x; sigdigits::Integer= [, base = 10])
```

`floor(x)`는 `x`보다 작거나 같은 `x`와 동일한 유형의 가장 가까운 정수 값을 반환합니다.

`floor(T, x)`는 결과를 유형 `T`로 변환하며, 바닥 값이 `T`로 표현할 수 없는 경우 `InexactError`를 발생시킵니다.

키워드 `digits`, `sigdigits` 및 `base`는 [`round`](@ref)와 동일하게 작동합니다.

새로운 유형에 대해 `floor`를 지원하려면 `Base.round(x::NewType, ::RoundingMode{:Down})`를 정의하십시오.
