```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

`(path, io)`를 반환합니다. 여기서 `path`는 `parent`에 있는 새 임시 파일의 경로이고, `io`는 이 경로에 대한 열린 파일 객체입니다. `cleanup` 옵션은 프로세스가 종료될 때 임시 파일이 자동으로 삭제되는지 여부를 제어합니다.

!!! compat "Julia 1.3"
    `cleanup` 키워드 인자는 Julia 1.3에서 추가되었습니다. 관련하여, 1.3부터 Julia는 `cleanup`이 명시적으로 `false`로 설정되지 않는 한, Julia 프로세스가 종료될 때 `mktemp`로 생성된 임시 경로를 제거합니다.

