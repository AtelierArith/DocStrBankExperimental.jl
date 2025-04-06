```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

`path`의 권한 모드를 `mode`로 변경합니다. 현재 정수 `mode`(예: `0o777`)만 지원됩니다. `recursive=true`이고 경로가 디렉토리인 경우 해당 디렉토리의 모든 권한이 재귀적으로 변경됩니다. `path`를 반환합니다.

!!! note
    Julia 1.6 이전에는 Windows에서 파일 시스템 ACL을 올바르게 조작하지 못했으므로 파일에 대해 읽기 전용 비트만 설정했습니다. 이제 ACL을 조작할 수 있습니다.

