```
ssh_pub_key_path() :: String
```

`ssh_pub_key_path()` 함수는 SSH 연결에 사용해야 하는 SSH 공개 키 파일의 경로를 반환합니다. `SSH_PUB_KEY_PATH` 환경 변수가 설정되어 있으면 해당 값을 반환합니다. 설정되어 있지 않지만 `SSH_KEY_PATH`가 설정되어 있으면 해당 경로에 `.pub` 접미사를 추가하여 반환합니다. 둘 다 설정되어 있지 않으면 기본적으로 다음을 반환합니다.

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

이 기본 값은 `SSH_DIR` 및 `SSH_KEY_NAME` 환경 변수에 따라 달라집니다.
