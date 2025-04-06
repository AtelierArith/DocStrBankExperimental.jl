```
Base.@constprop 설정 [ex]
```

주석이 달린 함수에 대한 절차 간 상수 전파 모드를 제어합니다.

두 가지 `설정`이 지원됩니다:

  * `Base.@constprop :aggressive [ex]`: 상수 전파를 공격적으로 적용합니다. 반환 유형이 인수의 값에 따라 달라지는 메서드의 경우, 추가 컴파일 시간의 대가로 향상된 추론 결과를 얻을 수 있습니다.
  * `Base.@constprop :none [ex]`: 상수 전파를 비활성화합니다. 이는 Julia가 그렇지 않으면 상수 전파에 적합하다고 판단할 수 있는 함수의 컴파일 시간을 줄일 수 있습니다. 일반적인 경우는 `Bool` 또는 `Symbol` 값의 인수 또는 키워드 인수를 가진 함수입니다.

`Base.@constprop`는 함수 정의 바로 앞이나 함수 본문 내에서 적용할 수 있습니다.

```julia
# 장황한 정의 주석 달기
Base.@constprop :aggressive function longdef(x)
    ...
end

# 간단한 정의 주석 달기
Base.@constprop :aggressive shortdef(x) = ...

# `do` 블록이 생성하는 익명 함수 주석 달기
f() do
    Base.@constprop :aggressive
    ...
end
```

!!! compat "Julia 1.10"
    함수 본문 내에서의 사용은 최소한 Julia 1.10이 필요합니다.

