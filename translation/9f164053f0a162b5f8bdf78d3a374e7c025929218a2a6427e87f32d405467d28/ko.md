# Using Valgrind with Julia

[Valgrind](https://valgrind.org/)는 메모리 디버깅, 메모리 누수 감지 및 프로파일링을 위한 도구입니다. 이 섹션에서는 Julia로 메모리 문제를 디버깅할 때 염두에 두어야 할 사항을 설명합니다.

## General considerations

기본적으로 Valgrind는 실행하는 프로그램에 자기 수정 코드가 없다고 가정합니다. 이 가정은 대부분의 경우 잘 작동하지만 `julia`와 같은 즉시 컴파일러에는 심각하게 실패합니다. 이러한 이유로 `--smc-check=all-non-file`를 `valgrind`에 전달하는 것이 중요하며, 그렇지 않으면 코드가 충돌하거나 예상치 못한 방식(종종 미묘한 방식으로)으로 동작할 수 있습니다.

일부 경우, Valgrind를 사용하여 메모리 오류를 더 잘 감지하기 위해 `julia`를 메모리 풀 비활성화 상태로 컴파일하는 것이 도움이 될 수 있습니다. 컴파일 타임 플래그 `MEMDEBUG`는 Julia에서 메모리 풀을 비활성화하고, `MEMDEBUG2`는 FemtoLisp에서 메모리 풀을 비활성화합니다. 두 플래그를 모두 사용하여 `julia`를 빌드하려면 `Make.user`에 다음 줄을 추가하세요:

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

또한 주목할 점은 프로그램이 여러 작업자 프로세스를 사용하는 경우, 부모 프로세스뿐만 아니라 모든 작업자 프로세스가 Valgrind에서 실행되기를 원할 가능성이 높다는 것입니다. 이를 위해 `--trace-children=yes`를 `valgrind`에 전달하십시오.

또 하나 주의할 점: `valgrind`를 사용할 때 `Unable to find compatible target in system image` 오류가 발생하면, `generic` 타겟으로 sysimage를 다시 빌드하거나 `JULIA_CPU_TARGET=generic`으로 줄리아를 빌드해 보세요.

## Suppressions

Valgrind는 실행 중에 일반적으로 잘못된 경고를 표시합니다. 이러한 경고의 수를 줄이기 위해 Valgrind에 [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress)를 제공하는 것이 도움이 됩니다. 샘플 억제 파일은 `contrib/valgrind-julia.supp`의 Julia 소스 배포판에 포함되어 있습니다.

`suppressions` 파일은 `julia/` 소스 디렉토리에서 다음과 같이 사용할 수 있습니다:

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

표시된 메모리 오류는 버그로 보고하거나 추가 억제를 기여해야 합니다. 일부 Valgrind 버전은 [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210)이므로, 버그를 제출하기 전에 고려해야 할 사항 중 하나일 수 있습니다.

## Running the Julia test suite under Valgrind

전체 Julia 테스트 스위트를 Valgrind에서 실행하는 것은 가능하지만, 상당한 시간이 걸립니다(일반적으로 몇 시간이 소요됨). 그렇게 하려면 `julia/test/` 디렉토리에서 다음 명령을 실행하세요:

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

"확실한" 메모리 누수 보고서를 보려면 `valgrind`에 `--leak-check=full --show-leak-kinds=definite` 플래그를 함께 전달하세요.

## Additional spurious warnings

이 섹션에서는 억제 파일에 추가할 수는 없지만 무시해도 안전한 Valgrind 경고를 다룹니다.

### Unhandled rr system calls

Valgrind는 [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h) 또는 [Record and Replay Framework](https://rr-project.org/)를 발견하면 경고를 발생시킵니다. 특히, julia가 rr 아래에서 실행되고 있는지 감지하려고 할 때 처리되지 않은 `1008` syscall에 대한 경고가 표시됩니다:

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

이 문제 [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) 를 Valgrind 개발자에게 요청한 대로 전달합니다.

## Caveats

Valgrind는 현재 [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779)이므로, 반올림 모드를 조정하는 코드는 Valgrind에서 실행될 때 다르게 동작할 것입니다.

일반적으로 `--smc-check=all-non-file`를 설정한 후 프로그램이 Valgrind에서 실행할 때 다르게 동작하는 경우, 추가 조사를 진행할 때 `valgrind`에 `--tool=none`을 전달하는 것이 도움이 될 수 있습니다. 이렇게 하면 최소한의 Valgrind 기계가 활성화되지만 전체 메모리 검사기가 활성화된 경우보다 훨씬 빠르게 실행됩니다.
