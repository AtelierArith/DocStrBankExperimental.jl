```
open(command, mode::AbstractString, stdio=devnull)
```

`command`를 비동기적으로 실행합니다. `open(command, stdio; read, write)`와 비슷하지만 키워드 인수 대신 모드 문자열을 통해 읽기 및 쓰기 플래그를 지정합니다. 가능한 모드 문자열은 다음과 같습니다:

| 모드   | 설명     | 키워드                         |
|:---- |:------ |:--------------------------- |
| `r`  | 읽기     | 없음                          |
| `w`  | 쓰기     | `write = true`              |
| `r+` | 읽기, 쓰기 | `read = true, write = true` |
| `w+` | 읽기, 쓰기 | `read = true, write = true` |
