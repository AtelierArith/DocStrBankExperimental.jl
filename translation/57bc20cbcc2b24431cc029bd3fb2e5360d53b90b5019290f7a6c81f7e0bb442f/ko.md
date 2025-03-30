```
dlsym_e(handle, sym)
```

공유 라이브러리 핸들에서 심볼을 조회하고, 조회 실패 시 조용히 `C_NULL`을 반환합니다. 이 메서드는 이제 `dlsym(handle, sym; throw_error=false)`를 선호하여 사용하지 않도록 권장됩니다.
