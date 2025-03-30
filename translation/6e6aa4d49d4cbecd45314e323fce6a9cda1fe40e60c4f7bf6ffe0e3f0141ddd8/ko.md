```
tryopen_exclusive(path::String, mode::Integer = 0o444) :: Union{Void, File}
```

읽기-쓰기 자문 전용 액세스를 위해 새 파일을 생성하려고 시도하며, 이미 존재하는 경우 아무것도 반환하지 않습니다.
