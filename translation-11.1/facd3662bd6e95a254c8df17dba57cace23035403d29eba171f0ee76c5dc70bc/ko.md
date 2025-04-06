```
SimpleLogger([stream,] min_level=Info)
```

모든 메시지를 `min_level` 이상으로 `stream`에 기록하는 단순 로거입니다. 스트림이 닫히면 경고 수준 이상인 메시지는 `stderr`에 기록되고 그 이하의 메시지는 `stdout`에 기록됩니다.
