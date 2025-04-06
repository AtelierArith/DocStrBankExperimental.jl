```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

`command`을 비동기적으로 실행하고 `process::IO` 객체를 반환합니다. `read`가 true이면 프로세스에서 읽는 내용은 프로세스의 표준 출력에서 오며, `stdio`는 선택적으로 프로세스의 표준 입력 스트림을 지정합니다. `write`가 true이면 쓰기는 프로세스의 표준 입력으로 가고, `stdio`는 선택적으로 프로세스의 표준 출력 스트림을 지정합니다. 프로세스의 표준 오류 스트림은 현재 전역 `stderr`에 연결됩니다.
