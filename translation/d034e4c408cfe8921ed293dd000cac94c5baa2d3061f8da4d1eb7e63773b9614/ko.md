```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

파일 또는 디렉토리 `path`의 변경 사항을 감시하며, 변경 사항이 발생하거나 `timeout_s` 초가 경과할 때까지 대기합니다. 이 함수는 파일 시스템을 폴링하지 않고, 대신 운영 체제에서 알림을 받기 위해 플랫폼별 기능을 사용합니다(예: Linux의 inotify를 통해). 자세한 내용은 아래에 링크된 NodeJS 문서를 참조하십시오.

반환된 값은 파일 감시 결과를 제공하는 불리언 필드 `renamed`, `changed`, `timedout`을 가진 객체입니다.

이 함수의 동작은 플랫폼에 따라 약간 다를 수 있습니다. 더 자세한 정보는 [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats)에서 확인하십시오.
