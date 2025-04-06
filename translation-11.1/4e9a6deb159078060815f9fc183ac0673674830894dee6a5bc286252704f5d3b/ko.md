```
WorkerConfig
```

[`ClusterManager`](@ref)에서 클러스터에 추가된 작업자를 제어하는 데 사용되는 유형입니다. 일부 필드는 모든 클러스터 관리자가 호스트에 접근하는 데 사용됩니다:

  * `io` – 작업자에 접근하는 데 사용되는 연결 (하위 유형 `IO` 또는 `Nothing`)
  * `host` – 호스트 주소 (문자열 `String` 또는 `Nothing`)
  * `port` – 작업자에 연결하는 데 사용되는 호스트의 포트 (정수 `Int` 또는 `Nothing`)

일부는 클러스터 관리자가 이미 초기화된 호스트에 작업자를 추가하는 데 사용됩니다:

  * `count` – 호스트에서 시작할 작업자의 수
  * `exename` – 호스트에서의 Julia 실행 파일 경로, 기본값은 `"$(Sys.BINDIR)/julia"` 또는 `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – 원격으로 Julia를 시작할 때 사용할 플래그

`userdata` 필드는 외부 관리자가 각 작업자에 대한 정보를 저장하는 데 사용됩니다.

일부 필드는 `SSHManager` 및 유사한 관리자에서 사용됩니다:

  * `tunnel` – `true` (터널링 사용), `false` (터널링 사용 안 함), 또는 [`nothing`](@ref) (관리자에 대한 기본값 사용)
  * `multiplex` – `true` (터널링을 위한 SSH 다중화 사용) 또는 `false`
  * `forward` – ssh의 `-L` 옵션에 사용되는 포워딩 옵션
  * `bind_addr` – 원격 호스트에서 바인딩할 주소
  * `sshflags` – SSH 연결을 설정할 때 사용할 플래그
  * `max_parallel` – 호스트에서 병렬로 연결할 수 있는 최대 작업자 수

일부 필드는 `LocalManager`와 `SSHManager` 모두에서 사용됩니다:

  * `connect_at` – 이것이 작업자 간의 설정 호출인지 드라이버에서 작업자로의 설정 호출인지 결정
  * `process` – 연결될 프로세스 (일반적으로 관리자가 [`addprocs`](@ref) 중에 이를 할당)
  * `ospid` – 호스트 OS에 따른 프로세스 ID, 작업자 프로세스를 중단하는 데 사용
  * `environ` – Local/SSH 관리자가 임시 정보를 저장하는 데 사용하는 개인 사전
  * `ident` – [`ClusterManager`](@ref)에 의해 식별된 작업자
  * `connect_idents` – 사용자 정의 토폴로지를 사용하는 경우 작업자가 연결해야 하는 작업자 ID 목록
  * `enable_threaded_blas` – `true`, `false`, 또는 `nothing`, 작업자에서 스레드화된 BLAS를 사용할지 여부
