```
dlsym(handle, sym; throw_error::Bool = true)
```

공유 라이브러리 핸들에서 심볼을 조회하고, 성공 시 호출 가능한 함수 포인터를 반환합니다.

심볼을 찾을 수 없는 경우, 이 메서드는 오류를 발생시키지만, 키워드 인수 `throw_error`가 `false`로 설정된 경우에는 이 메서드가 `nothing`을 반환합니다.
