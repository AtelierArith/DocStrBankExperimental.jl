```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

범위 `r`는 `r[i]`가 타입 `T`의 값을 생성하는 범위입니다(첫 번째 형태에서 `T`는 자동으로 유추됩니다). 이는 `ref` 값, `step`, 및 길이 `len`으로 매개변수화됩니다. 기본적으로 `ref`는 시작 값 `r[1]`이지만, 대안으로 다른 인덱스 `1 <= offset <= len`에 대해 `r[offset]`의 값으로 제공할 수 있습니다. `a:b` 또는 `a:b:c` 구문에서 `a`, `b`, 또는 `c`가 부동 소수점 숫자인 경우 `StepRangeLen`을 생성합니다.

!!! compat "Julia 1.7"
    4번째 타입 매개변수 `L`은 최소한 Julia 1.7이 필요합니다.

