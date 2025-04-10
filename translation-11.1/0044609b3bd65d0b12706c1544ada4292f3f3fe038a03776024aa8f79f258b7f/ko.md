```
tempname(parent=tempdir(); cleanup=true) -> String
```

임시 파일 경로를 생성합니다. 이 함수는 경로만 반환하며, 파일은 생성되지 않습니다. 경로는 고유할 가능성이 있지만, `tempname`에 대한 두 개의 동시 호출이 동일한 파일 이름을 생성할 가능성이 매우 낮기 때문에 보장할 수는 없습니다. 이름은 `tempname` 호출 시점에 이미 존재하는 모든 파일과 다를 것이 보장됩니다.

인수가 없는 상태로 호출되면, 임시 이름은 `tempdir()`에 의해 제공된 시스템 임시 디렉토리의 임시 이름에 대한 절대 경로가 됩니다. `parent` 디렉토리 인수가 주어지면, 임시 경로는 대신 해당 디렉토리에 위치하게 됩니다.

`cleanup` 옵션은 프로세스가 종료될 때 반환된 경로를 자동으로 삭제하려고 시도하는지 여부를 제어합니다. `tempname` 함수는 반환된 위치에 파일이나 디렉토리를 생성하지 않으므로, 그곳에 파일이나 디렉토리를 생성하지 않는 한 정리할 것이 없습니다. 만약 생성하고 `cleanup`이 `true`이면 프로세스 종료 시 삭제됩니다.

!!! compat "Julia 1.4"
    `parent` 및 `cleanup` 인수는 1.4에서 추가되었습니다. Julia 1.4 이전에는 `tempname`의 경로가 프로세스 종료 시 정리되지 않았습니다.


!!! warning
    다른 프로세스가 동일한 파일 이름을 얻고 당신이 파일을 생성하기 전에 파일을 생성하면 보안 구멍이 발생할 수 있습니다. 이 점이 우려된다면 `JL_O_EXCL`로 파일을 여세요. [`mktemp()`](@ref)를 사용하는 것도 권장됩니다.

