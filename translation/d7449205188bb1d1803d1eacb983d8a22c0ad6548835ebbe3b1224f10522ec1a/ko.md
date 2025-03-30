```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> 프로세스 식별자 목록
```

로컬 호스트에서 내장된 `LocalManager`를 사용하여 `np` 작업자를 시작합니다.

로컬 작업자는 현재 패키지 환경(즉, 활성 프로젝트, [`LOAD_PATH`](@ref), 및 [`DEPOT_PATH`](@ref))을 메인 프로세스에서 상속받습니다.

!!! 경고     작업자는 `~/.julia/config/startup.jl` 시작 스크립트를 실행하지 않으며, 다른 실행 중인 프로세스와 전역 상태(예: 명령줄 스위치, 전역 변수, 새로운 메서드 정의 및 로드된 모듈)를 동기화하지 않습니다.

**키워드 인수**:

  * `restrict::Bool`: `true`(기본값)인 경우 바인딩이 `127.0.0.1`로 제한됩니다.
  * `dir`, `exename`, `exeflags`, `env`, `topology`, `lazy`, `enable_threaded_blas`: `SSHManager`와 동일한 효과, [`addprocs(machines::AbstractVector)`](@ref) 문서를 참조하십시오.

!!! 호환성 "Julia 1.9"     패키지 환경의 상속과 `env` 키워드 인수는 Julia 1.9에서 추가되었습니다.
