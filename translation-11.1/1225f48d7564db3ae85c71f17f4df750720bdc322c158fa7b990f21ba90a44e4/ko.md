```
isequal(x)
```

`x`와 [`isequal`](@ref)를 사용하여 인수를 비교하는 함수를 만듭니다. 즉, `y -> isequal(y, x)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix2{typeof(isequal)}` 유형이며, 이는 특수화된 메서드를 구현하는 데 사용할 수 있습니다.
