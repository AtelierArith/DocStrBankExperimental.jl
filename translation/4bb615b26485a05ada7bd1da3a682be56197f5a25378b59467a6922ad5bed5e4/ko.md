```
unwatch_folder(path::AbstractString)
```

`path`에 대한 변경 사항의 백그라운드 추적을 중지합니다. 동일한 경로에서 `watch_folder`가 반환되기를 기다리는 다른 작업이 있는 동안 이 작업을 수행하는 것은 권장되지 않으며, 결과가 예측할 수 없을 수 있습니다.
