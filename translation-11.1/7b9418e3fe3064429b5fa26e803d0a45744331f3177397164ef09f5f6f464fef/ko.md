```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

이터레이터를 진행하여 다음 요소를 얻습니다. 남은 요소가 없으면 `nothing`이 반환되어야 합니다. 그렇지 않으면 다음 요소와 새로운 반복 상태의 2-튜플이 반환되어야 합니다.
