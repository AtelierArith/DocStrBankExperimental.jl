```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

CPU 프로파일링 줄리아 코드를 위한 두 가지 주요 접근 방식이 있습니다:

## Via `@profile`

주어진 호출에 대해 `@profile` 매크로를 통해 프로파일링이 활성화된 곳.

```julia-repl
julia> using Profile

julia> @profile foo()

julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
    ╎147  @Base/client.jl:506; _start()
        ╎ 147  @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...
```

## Triggered During Execution

이미 실행 중인 작업은 사용자 트리거 시간에 고정된 시간 동안 프로파일링할 수 있습니다.

프로파일링을 트리거하려면:

  * MacOS 및 FreeBSD (BSD 기반 플랫폼): `ctrl-t`를 사용하거나 `SIGINFO` 신호를 julia 프로세스에 전달합니다. 즉, `% kill -INFO $julia_pid`
  * Linux: `julia` 프로세스에 `SIGUSR1` 신호를 전달합니다. 즉, `% kill -USR1 $julia_pid`
  * Windows: 현재 지원되지 않음.

먼저, 신호가 발생한 순간의 단일 스택 추적이 표시되고, 그 다음 1초 프로파일이 수집되며, 다음 양보 지점에서 프로파일 보고서가 제공됩니다. 이는 양보 지점이 없는 코드(예: 타이트 루프)의 경우 작업 완료 시점일 수 있습니다.

Optionally set environment variable [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) to `1` to also automatically collect a [heap snapshot](@ref Heap-Snapshots).

```julia-repl
julia> foo()
##== the user sends a trigger while foo is running ==##
load: 2.53  cmd: julia 88903 running 6.16u 0.97s

======================================================================================
Information request received. A stacktrace will print followed by a 1.0 second profile
======================================================================================

signal (29): Information request: 29
__psynch_cvwait at /usr/lib/system/libsystem_kernel.dylib (unknown line)
_pthread_cond_wait at /usr/lib/system/libsystem_pthread.dylib (unknown line)
...

======================================================================
Profile collected. A report will print if the Profile module is loaded
======================================================================

Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
Thread 1 Task 0x000000011687c010 Total snapshots: 572. Utilization: 100%
   ╎147 @Base/client.jl:506; _start()
       ╎ 147 @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...

Thread 2 Task 0x0000000116960010 Total snapshots: 572. Utilization: 0%
   ╎572 @Base/task.jl:587; task_done_hook(t::Task)
      ╎ 572 @Base/task.jl:879; wait()
...
```

### Customization

프로파일링의 지속 시간은 [`Profile.set_peek_duration`](@ref)를 통해 조정할 수 있습니다.

프로필 보고서는 스레드와 작업별로 나뉩니다. 이를 재정의하려면 인수가 없는 함수를 `Profile.peek_report[]`에 전달하세요. 즉, `Profile.peek_report[] = () -> Profile.print()`를 사용하여 그룹화를 제거할 수 있습니다. 이는 외부 프로필 데이터 소비자에 의해 재정의될 수도 있습니다.

## Reference

```@docs
Profile.@profile
```

`Profile`의 메서드는 내보내지 않으며, 예를 들어 `Profile.print()`와 같이 호출해야 합니다.

```@docs
Profile.clear
Profile.print
Profile.init
Profile.fetch
Profile.retrieve
Profile.callers
Profile.clear_malloc_data
Profile.get_peek_duration
Profile.set_peek_duration
```

## Memory profiling

```@docs
Profile.Allocs.@profile
```

`Profile.Allocs`의 메서드는 내보내지 않으며, 예를 들어 `Profile.Allocs.fetch()`와 같이 호출해야 합니다.

```@docs
Profile.Allocs.clear
Profile.Allocs.print
Profile.Allocs.fetch
Profile.Allocs.start
Profile.Allocs.stop
```

## Heap Snapshots

```@docs
Profile.take_heap_snapshot
```

`Profile`의 메서드는 내보내지지 않으며, 예를 들어 `Profile.take_heap_snapshot()`과 같이 호출해야 합니다.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

힙에 있는 줄리아 객체의 추적 및 기록. 이는 줄리아 가비지 컬렉터에 의해 알려진 객체만 기록합니다. 가비지 컬렉터에 의해 관리되지 않는 외부 라이브러리에 의해 할당된 메모리는 스냅샷에 나타나지 않습니다.

스냅샷을 기록하는 동안 OOM을 피하기 위해, 힙 스냅샷을 네 개의 파일로 스트리밍할 수 있는 스트리밍 옵션을 추가했습니다.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

여기서 "snapshot"은 생성된 파일의 접두사로 사용되는 파일 경로입니다.

스냅샷 파일이 생성되면, 다음 명령어로 오프라인에서 조립할 수 있습니다:

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

결과적인 힙 스냅샷 파일은 Chrome DevTools에 업로드되어 볼 수 있습니다. 자세한 내용은 [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots)를 참조하세요. Chromium 힙 스냅샷을 분석하는 또 다른 방법은 VS Code 확장 `ms-vscode.vscode-js-profile-flame`을 사용하는 것입니다.

Firefox 힙 스냅샷은 다른 형식이며, 현재 Firefox는 Julia에 의해 생성된 힙 스냅샷을 보는 데 *사용할 수 없습니다*.
