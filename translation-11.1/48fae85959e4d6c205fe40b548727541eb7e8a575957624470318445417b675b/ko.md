```
ssh_key_pass() :: String
```

`ssh_key_pass()` 함수는 환경 변수 `SSH_KEY_PASS`가 설정되어 있으면 그 값을 반환하고, 설정되어 있지 않으면 `nothing`을 반환합니다. 미래에는 보안 시스템 저장소와 같은 다른 방법으로 비밀번호를 찾을 수 있을 것으로 예상되므로, SSH 개인 키를 복호화하는 데 비밀번호가 필요한 패키지는 환경 변수를 직접 확인하는 대신 이 API를 사용해야 하며, 이를 통해 추가될 때 자동으로 이러한 기능을 얻을 수 있습니다.
