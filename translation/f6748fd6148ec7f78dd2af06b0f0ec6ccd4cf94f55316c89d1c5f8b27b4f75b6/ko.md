```
addenv(command::Cmd, env...; inherit::Bool = true)
```

주어진 [`Cmd`](@ref) 객체에 새로운 환경 매핑을 병합하여 새로운 `Cmd` 객체를 반환합니다. 중복된 키는 대체됩니다. `command`에 이미 설정된 환경 값이 없으면, `inherit`가 `true`인 경우 `addenv()` 호출 시점의 현재 환경을 상속받습니다. 값이 `nothing`인 키는 환경에서 삭제됩니다.

또한 [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref)를 참조하세요.

!!! compat "Julia 1.6"
    이 함수는 Julia 1.6 이상이 필요합니다.

