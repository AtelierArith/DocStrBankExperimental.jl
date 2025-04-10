```
set_zero_subnormals(yes::Bool) -> Bool
```

`yes`가 `false`인 경우, 이후의 부동 소수점 연산은 비정상 값("denormals")에 대한 IEEE 산술 규칙을 따릅니다. 그렇지 않으면, 부동 소수점 연산은 비정상 입력 또는 출력을 0으로 변환하는 것이 허용되지만 필수는 아닙니다. `true`를 반환하지만 `yes==true`이고 하드웨어가 비정상 숫자의 0화를 지원하지 않는 경우는 제외입니다.

`set_zero_subnormals(true)`는 일부 하드웨어에서 일부 계산을 가속화할 수 있습니다. 그러나 `(x-y==0) == (x==y)`와 같은 항등식을 깨뜨릴 수 있습니다.

!!! 경고     이 함수는 현재 스레드에만 영향을 미칩니다.
