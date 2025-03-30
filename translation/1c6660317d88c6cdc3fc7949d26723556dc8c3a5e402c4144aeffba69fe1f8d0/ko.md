```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

주어진 `prefix`와 무작위 접미사로 구성된 이름을 가진 임시 디렉토리를 `parent` 디렉토리에 생성하고 그 경로를 반환합니다. 또한, 일부 플랫폼에서는 `prefix`의 끝에 있는 `'X'` 문자가 무작위 문자로 대체될 수 있습니다. `parent`가 존재하지 않으면 오류를 발생시킵니다. `cleanup` 옵션은 프로세스가 종료될 때 임시 디렉토리가 자동으로 삭제되는지 여부를 제어합니다.

!!! compat "Julia 1.2"
    `prefix` 키워드 인자는 Julia 1.2에서 추가되었습니다.


!!! compat "Julia 1.3"
    `cleanup` 키워드 인자는 Julia 1.3에서 추가되었습니다. 관련하여, 1.3부터 Julia는 `cleanup`이 명시적으로 `false`로 설정되지 않는 한, Julia 프로세스가 종료될 때 `mktempdir`로 생성된 임시 경로를 제거합니다.


참고: [`mktemp`](@ref), [`mkdir`](@ref).
