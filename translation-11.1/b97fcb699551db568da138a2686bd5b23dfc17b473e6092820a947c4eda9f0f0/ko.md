```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

파일을 다섯 개의 불리언 키워드 인수로 지정된 모드로 엽니다:

| 키워드        | 설명          | 기본값                                   |
|:---------- |:----------- |:------------------------------------- |
| `read`     | 읽기 위해 열기    | `!write`                              |
| `write`    | 쓰기 위해 열기    | `truncate \| append`                  |
| `create`   | 존재하지 않으면 생성 | `!read & write \| truncate \| append` |
| `truncate` | 크기를 0으로 자르기 | `!read & write`                       |
| `append`   | 끝으로 이동      | `false`                               |

키워드가 전달되지 않으면 기본적으로 파일을 읽기 전용으로 엽니다. 열린 파일에 접근하기 위한 스트림을 반환합니다.

`lock` 키워드 인수는 안전한 다중 스레드 접근을 위해 작업이 잠길지 여부를 제어합니다.

!!! compat "Julia 1.5"
    `lock` 인수는 Julia 1.5부터 사용할 수 있습니다.

