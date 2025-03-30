```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

새로운 `Cmd` 객체를 생성하여 외부 프로그램과 인수를 나타내며, 선택적 키워드 인수의 설정을 변경합니다:

  * `ignorestatus::Bool`: `true`인 경우(기본값은 `false`), `Cmd`는 반환 코드가 0이 아닐 경우 오류를 발생시키지 않습니다.
  * `detach::Bool`: `true`인 경우(기본값은 `false`), `Cmd`는 새로운 프로세스 그룹에서 실행되어 `julia` 프로세스보다 오래 살아남을 수 있으며, Ctrl-C가 전달되지 않습니다.
  * `windows_verbatim::Bool`: `true`인 경우(기본값은 `false`), Windows에서 `Cmd`는 인수에 대한 인용이나 이스케이프 없이 프로세스에 명령줄 문자열을 보냅니다. (Windows에서는 인수가 프로그램에 단일 "명령줄" 문자열로 전송되며, 프로그램은 이를 인수로 구문 분석하는 책임이 있습니다. 기본적으로 빈 인수와 공백 또는 탭이 포함된 인수는 명령줄에서 큰따옴표 `"`로 인용되며, `\` 또는 `"`는 백슬래시로 앞에 붙습니다. `windows_verbatim=true`는 비표준 방식으로 명령줄을 구문 분석하는 프로그램을 실행하는 데 유용합니다.) 비-Windows 시스템에는 영향을 미치지 않습니다.
  * `windows_hide::Bool`: `true`인 경우(기본값은 `false`), Windows에서 `Cmd`가 실행될 때 새로운 콘솔 창이 표시되지 않습니다. 이미 콘솔이 열려 있거나 비-Windows 시스템에서는 영향을 미치지 않습니다.
  * `env`: `Cmd`를 실행할 때 사용할 환경 변수를 설정합니다. `env`는 문자열을 문자열에 매핑하는 사전, `"var=val"` 형식의 문자열 배열, `"var"=>val` 쌍의 배열 또는 튜플일 수 있습니다. 기존 환경을 수정(대체가 아닌)하려면 `env`를 `copy(ENV)`로 초기화한 다음 원하는 대로 `env["var"]=val`을 설정합니다. 모든 요소를 대체하지 않고 `Cmd` 객체 내의 환경 블록에 추가하려면 [`addenv()`](@ref)를 사용하여 업데이트된 환경을 가진 `Cmd` 객체를 반환합니다.
  * `dir::AbstractString`: 명령을 위한 작업 디렉토리를 지정합니다(현재 디렉토리 대신).

지정되지 않은 키워드에 대해서는 `cmd`의 현재 설정이 사용됩니다.

`Cmd(exec)` 생성자는 `exec`의 복사본을 생성하지 않는다는 점에 유의하십시오. `exec`에 대한 이후 변경 사항은 `Cmd` 객체에 반영됩니다.

`Cmd` 객체를 생성하는 가장 일반적인 방법은 명령 리터럴(백틱)을 사용하는 것입니다. 예를 들어:

```
`ls -l`
```

이것은 `Cmd` 생성자에 전달되어 설정을 수정할 수 있습니다. 예를 들어:

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
