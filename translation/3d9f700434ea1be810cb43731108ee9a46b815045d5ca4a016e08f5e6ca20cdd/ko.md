```
notify(condition, val=nothing; all=true, error=false)
```

조건을 기다리고 있는 작업을 깨우고, `val`을 전달합니다. `all`이 `true`(기본값)인 경우 모든 대기 작업이 깨워지며, 그렇지 않으면 하나만 깨워집니다. `error`가 `true`인 경우, 전달된 값이 깨워진 작업에서 예외로 발생합니다.

깨워진 작업의 수를 반환합니다. `condition`에서 대기 중인 작업이 없으면 0을 반환합니다.
