```
task_local_storage(body, key, value)
```

`value`가 `key`에 할당된 수정된 작업-로컬 저장소로 `body` 함수를 호출합니다. `key`의 이전 값 또는 그 부재는 이후에 복원됩니다. 동적 범위를 에뮬레이션하는 데 유용합니다.
