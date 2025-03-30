```
ssh_key_path() :: String
```

`ssh_key_path()` 함수는 SSH 연결에 사용해야 하는 SSH 개인 키 파일의 경로를 반환합니다. `SSH_KEY_PATH` 환경 변수가 설정되어 있으면 해당 값을 반환합니다. 그렇지 않으면 기본적으로 다음을 반환합니다.

```
joinpath(ssh_dir(), ssh_key_name())
```

이 기본 값은 `SSH_DIR` 및 `SSH_KEY_NAME` 환경 변수에 따라 달라집니다.
