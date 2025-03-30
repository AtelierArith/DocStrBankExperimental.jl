```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

`io`에 프로파일링 결과를 출력합니다(기본값은 `stdout`). `data` 벡터를 제공하지 않으면, 누적된 백트레이스의 내부 버퍼가 사용됩니다.

유효한 키워드 인수에 대한 설명은 `Profile.print`를 참조하세요.
