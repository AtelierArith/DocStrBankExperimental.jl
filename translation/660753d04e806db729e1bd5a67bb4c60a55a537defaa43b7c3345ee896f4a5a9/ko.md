```
issetequal(x)
```

`x`와 [`issetequal`](@ref)를 사용하여 인수를 비교하는 함수를 만듭니다. 즉, `y -> issetequal(y, x)`와 동등한 함수입니다. 반환된 함수는 `Base.Fix2{typeof(issetequal)}` 유형이며, 이는 특수화된 메서드를 구현하는 데 사용할 수 있습니다.

!!! compat "Julia 1.11"
    이 기능은 최소한 Julia 1.11이 필요합니다.

