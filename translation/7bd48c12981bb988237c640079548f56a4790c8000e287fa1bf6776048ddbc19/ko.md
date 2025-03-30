```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

`N` 개의 중첩 루프를 생성하며, `itersym`을 반복 변수의 접두사로 사용합니다. `rangeexpr`는 익명 함수 표현식일 수도 있고, 간단한 기호 `var`일 경우에는 범위가 차원 `d`에 대해 `axes(var, d)`가 됩니다.

선택적으로 "pre" 및 "post" 표현식을 제공할 수 있습니다. 이들은 각각 각 루프의 본문에서 처음과 마지막에 실행됩니다. 예를 들어:

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

는 다음과 같이 생성됩니다:

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

단지 post-expression만 원한다면, pre-expression에 [`nothing`](@ref)를 공급하십시오. 괄호와 세미콜론을 사용하여 다중 문장 표현식을 제공할 수 있습니다.
