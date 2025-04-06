```
indexpids(S::SharedArray)
```

현재 작업자의 인덱스를 `SharedArray`의 작업자 목록에서 반환합니다(즉, `procs(S)`에 의해 반환된 동일한 목록에서). `SharedArray`가 로컬로 매핑되지 않은 경우 0을 반환합니다.
