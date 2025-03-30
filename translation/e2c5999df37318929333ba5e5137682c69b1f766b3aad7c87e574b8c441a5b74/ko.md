```
isreadable(path::String)
```

주어진 `path`에 대한 접근 권한이 현재 사용자에 의해 읽기가 허용되면 `true`를 반환합니다.

!!! note
    이 권한은 사용자가 `open`을 호출하기 전에 변경될 수 있으므로, `isreadable`을 먼저 호출하기보다는 `open`만 호출하고 실패할 경우 오류를 처리하는 것이 좋습니다.


!!! note
    현재 이 함수는 Windows에서 파일 시스템 ACL을 올바르게 조사하지 않으므로 잘못된 결과를 반환할 수 있습니다.


!!! compat "Julia 1.11"
    이 함수는 최소한 Julia 1.11이 필요합니다.


또한 [`ispath`](@ref), [`isexecutable`](@ref), [`iswritable`](@ref)를 참조하세요.
