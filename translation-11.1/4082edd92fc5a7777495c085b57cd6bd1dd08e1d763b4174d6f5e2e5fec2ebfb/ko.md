```
isexecutable(path::String)
```

주어진 `path`에 실행 권한이 있으면 `true`를 반환합니다.

!!! note
    이 권한은 사용자가 `path`를 실행하기 전에 변경될 수 있으므로, `isexecutable`을 먼저 호출하기보다는 파일을 실행하고 실패할 경우 오류를 처리하는 것이 좋습니다.


!!! note
    Julia 1.6 이전에는 Windows에서 파일 시스템 ACL을 올바르게 조사하지 않았으므로, 모든 파일에 대해 `true`를 반환했습니다. Julia 1.6부터는 파일이 실행 가능으로 표시되어 있는지 여부를 올바르게 판단합니다.


또한 [`ispath`](@ref), [`isreadable`](@ref), [`iswritable`](@ref)를 참조하세요.
