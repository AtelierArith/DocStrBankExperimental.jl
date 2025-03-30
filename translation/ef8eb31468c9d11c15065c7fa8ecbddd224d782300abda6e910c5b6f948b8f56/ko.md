```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

우리의 pidfile 형식을 파싱하려고 시도하며, 실패한 읽기에 대해 각각 (0, "", 0.0)으로 요소를 대체합니다.
