```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

현재 프로세스 또는 pid 또는 proc로 식별된 프로세스에 대해 경로 "at"에 대한 pidfile 잠금을 생성합니다. 잠금이 설정된 후 `do` 블록에서 실행할 함수를 사용할 수 있으며, 이후 잠금은 자동으로 닫힙니다. 잠금에 실패하고 `wait`가 false인 경우 오류가 발생합니다.

잠금은 `close`, `finalizer` 또는 `proc`가 종료된 직후에 해제됩니다. 반환 값이 프로그램의 중요한 섹션 끝까지 살아 있도록 하여 `finalizer`가 이를 조기에 회수하지 않도록 하십시오.

선택적 키워드 인수:

  * `mode`: 파일 접근 모드(프로세스 umask에 의해 수정됨). 기본값은 모든 사용자에게 읽기 가능.
  * `poll_interval`: 시도 간 최대 시간을 지정합니다(만약 `watch_file`이 작동하지 않는 경우).
  * `stale_age`: 기존 pidfile을 삭제합니다(잠금을 무시하고) 이 많은 초보다 오래된 경우, mtime을 기준으로 합니다. 파일이 유효할 수 있는 pid가 나타나면 이보다 5배 더 긴 시간 동안 삭제되지 않습니다. 또는 `refresh`가 0으로 재정의되어 잠금 새로 고침이 비활성화된 경우 25배 더 긴 시간 동안 삭제되지 않습니다. 기본적으로 이는 비활성화되어 있습니다(`stale_age` = 0), 그러나 일반적으로 권장되는 값은 예상 정상 완료 시간의 약 3-5배입니다.
  * `refresh`: 시간이 경과할 때마다 mtime을 업데이트하여 잠금이 오래되지 않도록 유지합니다. 기본적으로 이는 `stale_age/2`로 설정되어 있으며, 이는 권장 값입니다.
  * `wait`: true인 경우 잠금을 얻을 때까지 차단하고, false인 경우 잠금 실패 시 오류를 발생시킵니다.
