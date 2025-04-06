# Reporting and analyzing crashes (segfaults)

그래서 당신은 줄리아를 고장내는 데 성공했습니다. 축하합니다! 여기에는 문제가 발생했을 때 겪는 일반적인 증상에 대한 몇 가지 절차가 수집되어 있습니다. 이러한 디버깅 단계의 정보를 포함하는 것은 세그폴트 문제를 추적하거나 스크립트가 예상보다 느리게 실행되는 이유를 파악할 때 유지 관리자가 큰 도움이 될 수 있습니다.

이 페이지로 안내받았다면, 귀하가 경험하고 있는 증상과 가장 잘 일치하는 것을 찾아 요청된 디버깅 정보를 생성하기 위한 지침을 따르십시오. 증상 표:

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

오류와 관계없이, 우리는 항상 당신이 실행 중인 Julia의 버전을 알아야 합니다. Julia가 처음 시작될 때, 버전 번호와 날짜가 포함된 헤더가 출력됩니다. 또한, 생성하는 보고서에 `versioninfo()`의 출력(표준 라이브러리에서 내보낸 [`InteractiveUtils`](@ref InteractiveUtils.versioninfo) 포함)을 포함해 주세요:

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

`make` 프로세스의 끝부분에서 발생하는 세그멘테이션 오류는 Julia가 `base/` 폴더의 코드 집합을 미리 파싱하는 동안 문제가 발생하고 있다는 일반적인 증상입니다. 이 과정이 예기치 않게 종료되는 데는 여러 요인이 있을 수 있지만, 종종 Julia의 C 코드 부분에서 발생하는 오류 때문이며, 따라서 일반적으로 `gdb` 내에서 디버그 빌드를 사용하여 디버깅해야 합니다. 명시적으로:

Julia의 디버그 빌드를 생성하려면:

```
$ cd <julia_root>
$ make debug
```

이 프로세스는 일반 `make` 주문과 동일한 오류로 실패할 가능성이 높지만, 이는 `gdb`가 정확한 백트레이스를 얻기 위해 필요한 디버깅 기호를 제공하는 디버그 실행 파일을 생성합니다. 다음으로, `gdb` 내에서 부트스트랩 프로세스를 수동으로 실행하십시오:

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

이것은 `gdb`를 시작하고, 디버그 빌드의 Julia를 사용하여 부트스트랩 프로세스를 실행하려고 시도하며, 세그멘테이션 오류가 발생할 경우 백트레이스를 출력합니다. 전체 백트레이스를 얻기 위해 `<enter>`를 몇 번 눌러야 할 수도 있습니다. 백트레이스와 함께 [gist](https://gist.github.com), [version info](@ref dev-version-info), 그리고 생각할 수 있는 기타 관련 정보를 생성하고, 새로운 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)를 Github에서 열어 gist에 대한 링크를 포함하세요.

## Segfaults when running a script

절차는 [Segfaults during bootstrap (`sysimg.jl`)](@ref)와 매우 유사합니다. Julia의 디버그 빌드를 생성하고, 디버그된 Julia 프로세스 내에서 스크립트를 실행하십시오:

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

`gdb`는 그곳에 앉아 명령을 기다립니다. 프로세스를 실행하려면 `r`을 입력하고, 세그멘테이션 오류가 발생하면 백트레이스를 생성하려면 `bt`를 입력하세요:

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

[gist](https://gist.github.com)의 백트레이스를 생성하고, [version info](@ref dev-version-info) 및 생각할 수 있는 기타 관련 정보를 추가한 후, 새로운 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)를 Github에 열고 gist에 대한 링크를 포함하세요.

## Errors during Julia startup

가끔 Julia의 시작 과정에서 오류가 발생합니다(특히 소스에서 컴파일하는 대신 바이너리 배포판을 사용할 때) 다음과 같은 오류가 발생할 수 있습니다:

```julia
$ julia
exec: error -5
```

이러한 오류는 일반적으로 부팅 단계에서 무언가가 제대로 로드되지 않고 있음을 나타내며, 문제가 무엇인지 파악하는 가장 좋은 방법은 외부 도구를 사용하여 `julia` 프로세스의 디스크 활동을 감사하는 것입니다:

  * Linux에서 `strace` 사용:

    ```
    $ strace julia
    ```
  * OSX에서는 `dtruss`를 사용하세요:

    ```
    $ dtruss -f julia
    ```

[gist](https://gist.github.com)를 생성하고 `strace`/ `dtruss` 출력을 포함하며, [version info](@ref dev-version-info) 및 기타 관련 정보를 추가한 후, 새로운 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)를 Github에 열고 gist에 대한 링크를 포함하세요.

## Other generic segfaults or unreachables reached

다른 곳에서 언급했듯이, `julia`는 트레이스를 생성하기 위해 `rr`와 좋은 통합을 가지고 있습니다. 여기에는 Linux에서 `julia`를 `rr` 아래에서 자동으로 실행하고 충돌 후에 트레이스를 공유하는 기능이 포함됩니다. 이는 이러한 충돌을 디버깅할 때 매우 유용할 수 있으며, JuliaLang/julia 레포에 충돌 문제를 보고할 때 강력히 권장됩니다. `julia`를 `rr` 아래에서 자동으로 실행하려면 다음을 수행하십시오:

```julia
julia --bug-report=rr
```

로컬에서 `rr` 트레이스를 생성하되 공유하지 않으려면 다음과 같이 할 수 있습니다:

```julia
julia --bug-report=rr-local
```

이것은 Linux에서만 작동합니다. [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/)에 대한 블로그 게시물에는 더 많은 세부 정보가 있습니다.

## Glossary

이 가이드에서는 몇 가지 용어가 약어로 사용되었습니다:

  * `<julia_root>`는 Julia 소스 트리의 루트 디렉토리를 나타냅니다. 예를 들어, `base`, `deps`, `src`, `test` 등의 폴더가 포함되어야 합니다.....
