```
ssh_known_hosts_file() :: String
```

`ssh_known_hosts_file()` 함수는 SSH 연결을 위한 원격 서버의 신원을 설정할 때 사용해야 하는 SSH 알려진 호스트 파일의 단일 경로를 반환합니다. 실제로 존재하는 `ssh_known_hosts_files`에 의해 반환된 첫 번째 경로를 반환합니다. 여러 알려진 호스트 파일을 확인할 수 있는 호출자는 대신 `ssh_known_hosts_files`를 사용하고 해당 함수의 문서에 설명된 대로 반환된 모든 파일에서 호스트 일치를 찾아야 합니다.
