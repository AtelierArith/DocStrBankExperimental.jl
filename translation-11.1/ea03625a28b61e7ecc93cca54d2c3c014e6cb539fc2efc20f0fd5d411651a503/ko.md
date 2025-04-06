```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> 프로세스 식별자 목록
```

원격 머신에서 SSH를 통해 작업자 프로세스를 추가합니다. 구성은 키워드 인수로 수행됩니다(아래 참조). 특히, `exename` 키워드를 사용하여 원격 머신에서 `julia` 바이너리의 경로를 지정할 수 있습니다.

`machines`는 "[user@]host[:port] [bind*addr[:port]]" 형식의 문자열로 주어진 "머신 사양"의 벡터입니다. `user`는 현재 사용자로 기본 설정되며, `port`는 표준 SSH 포트로 기본 설정됩니다. `[bind*addr[:port]]`가 지정되면 다른 작업자는 지정된`bind_addr`및`port`에서 이 작업자에 연결합니다.

`machines` 벡터에서 튜플을 사용하거나 `(machine_spec, count)` 형식을 사용하여 원격 호스트에서 여러 프로세스를 시작할 수 있습니다. 여기서 `count`는 지정된 호스트에서 시작할 작업자의 수입니다. 작업자 수로 `:auto`를 전달하면 원격 호스트의 CPU 스레드 수만큼 작업자가 시작됩니다.

**예제**:

```julia
addprocs([
    "remote1",               # 현재 사용자 이름으로 로그인하여 'remote1'에서 하나의 작업자
    "user@remote2",          # 'user' 사용자 이름으로 로그인하여 'remote2'에서 하나의 작업자
    "user@remote3:2222",     # 'remote3'에 대해 SSH 포트를 '2222'로 지정
    ("user@remote4", 4),     # 'remote4'에서 4개의 작업자 시작
    ("user@remote5", :auto), # 'remote5'에서 CPU 스레드 수만큼 작업자 시작
])
```

**키워드 인수**:

  * `tunnel`: `true`인 경우 마스터 프로세스에서 작업자에 연결하기 위해 SSH 터널링이 사용됩니다. 기본값은 `false`입니다.
  * `multiplex`: `true`인 경우 SSH 터널링을 위해 SSH 다중화가 사용됩니다. 기본값은 `false`입니다.
  * `ssh`: 작업자를 시작하는 데 사용되는 SSH 클라이언트 실행 파일의 이름 또는 경로입니다. 기본값은 `"ssh"`입니다.
  * `sshflags`: 추가 ssh 옵션을 지정합니다. 예: ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`: 호스트에서 동시에 연결할 수 있는 최대 작업자 수를 지정합니다. 기본값은 10입니다.
  * `shell`: 작업자에서 ssh가 연결되는 셸의 유형을 지정합니다.

      * `shell=:posix`: POSIX 호환 Unix/Linux 셸(sh, ksh, bash, dash, zsh 등). 기본값입니다.
      * `shell=:csh`: Unix C 셸(csh, tcsh).
      * `shell=:wincmd`: Microsoft Windows `cmd.exe`.
  * `dir`: 작업자에서의 작업 디렉토리를 지정합니다. 기본값은 호스트의 현재 디렉토리(`pwd()`로 찾은)입니다.
  * `enable_threaded_blas`: `true`인 경우 추가된 프로세스에서 BLAS가 여러 스레드에서 실행됩니다. 기본값은 `false`입니다.
  * `exename`: `julia` 실행 파일의 이름입니다. 기본값은 `"$(Sys.BINDIR)/julia"` 또는 `"$(Sys.BINDIR)/julia-debug"`입니다. 모든 원격 머신에서 공통의 Julia 버전을 사용하는 것이 좋습니다. 그렇지 않으면 직렬화 및 코드 배포가 실패할 수 있습니다.
  * `exeflags`: 작업자 프로세스에 전달되는 추가 플래그입니다.
  * `topology`: 작업자가 서로 연결되는 방식을 지정합니다. 연결되지 않은 작업자 간의 메시지 전송은 오류를 발생시킵니다.

      * `topology=:all_to_all`: 모든 프로세스가 서로 연결되어 있습니다. 기본값입니다.
      * `topology=:master_worker`: 드라이버 프로세스, 즉 `pid` 1만 작업자에 연결됩니다. 작업자는 서로 연결되지 않습니다.
      * `topology=:custom`: 클러스터 관리자의 `launch` 메서드가 `WorkerConfig`의 `ident` 및 `connect_idents` 필드를 통해 연결 토폴로지를 지정합니다. 클러스터 관리자 ID `ident`를 가진 작업자는 `connect_idents`에 지정된 모든 작업자에 연결됩니다.
  * `lazy`: `topology=:all_to_all`에만 적용됩니다. `true`인 경우 작업자 간의 연결이 지연 설정됩니다. 즉, 작업자 간의 원격 호출의 첫 번째 인스턴스에서 설정됩니다. 기본값은 true입니다.
  * `env`: `env=["JULIA_DEPOT_PATH"=>"/depot"]`와 같은 문자열 쌍의 배열을 제공하여 원격 머신에서 환경 변수가 설정되도록 요청합니다. 기본적으로 `JULIA_WORKER_TIMEOUT` 환경 변수만 로컬에서 원격 환경으로 자동으로 전달됩니다.
  * `cmdline_cookie`: `--worker` 명령줄 옵션을 통해 인증 쿠키를 전달합니다. SSH stdio를 통해 쿠키를 전달하는 (더 안전한) 기본 동작은 이전 (ConPTY 이전) Julia 또는 Windows 버전을 사용하는 Windows 작업자와 함께 중단될 수 있으며, 이 경우 `cmdline_cookie=true`가 해결 방법을 제공합니다.

!!! compat "Julia 1.6"
    키워드 인수 `ssh`, `shell`, `env` 및 `cmdline_cookie`는 Julia 1.6에서 추가되었습니다.


환경 변수:

마스터 프로세스가 새로 시작된 작업자와 60.0초 이내에 연결을 설정하지 못하면 작업자는 이를 치명적인 상황으로 간주하고 종료합니다. 이 타임아웃은 환경 변수 `JULIA_WORKER_TIMEOUT`를 통해 제어할 수 있습니다. 마스터 프로세스에서 `JULIA_WORKER_TIMEOUT`의 값은 새로 시작된 작업자가 연결 설정을 기다리는 초 수를 지정합니다.
