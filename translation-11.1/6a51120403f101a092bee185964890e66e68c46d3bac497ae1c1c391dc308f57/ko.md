# Instrumenting Julia with DTrace, and bpftrace

DTrace와 bpftrace는 프로세스의 경량 계측을 가능하게 하는 도구입니다. 프로세스가 실행되는 동안 계측을 켜고 끌 수 있으며, 계측이 꺼져 있을 때는 오버헤드가 최소화됩니다.

!!! compat "Julia 1.8"
    Julia 1.8에서 프로브에 대한 지원이 추가되었습니다.


!!! note
    이 문서는 리눅스 관점에서 작성되었으며, 대부분의 내용은 Mac OS/Darwin 및 FreeBSD에서도 적용될 것입니다.


## Enabling support

리눅스에서 `dtrace` 버전이 포함된 `systemtap` 패키지를 설치하고 `Make.user` 파일을 생성합니다.

```
WITH_DTRACE=1
```

USDT 프로브를 활성화합니다.

### Verifying

```
> readelf -n usr/lib/libjulia-internal.so.1

Displaying notes found in: .note.gnu.build-id
  Owner                Data size  Description
  GNU                  0x00000014 NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 57161002f35548772a87418d2385c284ceb3ead8

Displaying notes found in: .note.stapsdt
  Owner                Data size  Description
  stapsdt              0x00000029 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__begin
    Location: 0x000000000013213e, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cac
    Arguments:
  stapsdt              0x00000032 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__stop_the_world
    Location: 0x0000000000132144, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cae
    Arguments:
  stapsdt              0x00000027 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__end
    Location: 0x000000000013214a, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb0
    Arguments:
  stapsdt              0x0000002d NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__finalizer
    Location: 0x0000000000132150, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb2
    Arguments:
```

## Adding probes in libjulia

프로브는 `src/uprobes.d` 파일에서 dtraces 형식으로 선언됩니다. 생성된 헤더 파일은 `src/julia_internal.h`에 포함되며, 프로브를 추가하는 경우 해당 파일에 noop 구현을 제공해야 합니다.

헤더에는 세마포어 `*_ENABLED`와 프로브에 대한 실제 호출이 포함됩니다. 프로브 인수가 계산하기 비싼 경우, 먼저 프로브가 활성화되어 있는지 확인한 다음 인수를 계산하고 프로브를 호출해야 합니다.

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

인수가 없는 프로브의 경우 세마포어 검사를 포함하지 않는 것이 바람직합니다. USDT 프로브가 활성화된 경우 세마포어의 비용은 프로브가 활성화되었는지 여부와 관계없이 메모리 로드입니다.

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

프로브 자체는 noop 슬레드로, 프로브 핸들러에 트램폴린으로 패치될 것입니다.

## Available probes

### GC probes

1. `julia:gc__begin`: GC가 하나의 스레드에서 실행을 시작하고 세상을 멈추는 트리거를 발생시킵니다.
2. `julia:gc__stop_the_world`: 모든 스레드가 안전 지점에 도달했으며 GC가 실행됩니다.
3. `julia:gc__mark__begin`: 마크 단계 시작
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: 마크 단계가 종료되었습니다.
5. `julia:gc__sweep_begin(full)`: 스윕 시작
6. `julia:gc__sweep_end`: 스윕 단계가 완료되었습니다.
7. `julia:gc__end`: GC가 완료되었습니다. 다른 스레드는 작업을 계속합니다.
8. `julia:gc__finalizer`: 초기 GC 스레드가 파이널라이저 실행을 완료했습니다.

### Task runtime probes

1. `julia:rt__run__task(task)`: 현재 스레드에서 작업 `task`로 전환합니다.
2. `julia:rt__pause__task(task)`: 현재 스레드에서 작업 `task`로 전환 중입니다.
3. `julia:rt__new__task(parent, child)`: 작업 `parent`가 현재 스레드에서 작업 `child`를 생성했습니다.
4. `julia:rt__start__task(task)`: 작업 `task`가 새로운 스택으로 처음 시작되었습니다.
5. `julia:rt__finish__task(task)`: 작업 `task`가 완료되었으며 더 이상 실행되지 않습니다.
6. `julia:rt__start__process__events(task)`: 작업 `task`가 libuv 이벤트 처리를 시작했습니다.
7. `julia:rt__finish__process__events(task)`: 작업 `task`가 libuv 이벤트 처리를 완료했습니다.

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: 스레드 `ptls`가 PARTR 다중 큐에 `task`를 삽입하려고 시도했습니다.
2. `julia:rt__taskq__get(ptls, task)`: 스레드 `ptls`가 PARTR 다중 큐에서 `task`를 꺼냈습니다.

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, old_state)`: 스레드 (PTLS `ptls`)가 이전 상태 `old_state`에서 깨어납니다.
2. `julia:rt__sleep__check__wakeup(ptls)`: 스레드 (PTLS `ptls`)가 스스로 깨어났습니다.
3. `julia:rt__sleep__check__sleep(ptls)`: 스레드 (PTLS `ptls`)가 잠자기를 시도하고 있습니다.
4. `julia:rt__sleep__check__taskq__wake(ptls)`: 스레드 (PTLS `ptls`)가 PARTR 다중 큐의 작업으로 인해 잠들지 못합니다.
5. `julia:rt__sleep__check__task__wake(ptls)`: 스레드 (PTLS `ptls`)가 Base 작업 대기열의 작업으로 인해 잠들지 못합니다.
6. `julia:rt__sleep__check__uv__wake(ptls)`: 스레드 (PTLS `ptls`)가 libuv 웨이크업으로 인해 잠들지 못했습니다.

## Probe usage examples

### GC stop-the-world latency

예제 `bpftrace` 스크립트는 `contrib/gc_stop_the_world_latency.bt`에 제공되며, 모든 스레드가 안전 지점에 도달하는 지연 시간의 히스토그램을 생성합니다.

이 Julia 코드를 실행하면 `julia -t 2`

```
using Base.Threads

fib(x) = x <= 1 ? 1 : fib(x-1) + fib(x-2)

beaver = @spawn begin
    while true
        fib(30)
        # A manual safepoint is necessary since otherwise this loop
        # may never yield to GC.
        GC.safepoint()
    end
end

allocator = @spawn begin
    while true
        zeros(1024)
    end
end

wait(allocator)
```

그리고 두 번째 터미널에서

```
> sudo contrib/bpftrace/gc_stop_the_world_latency.bt
Attaching 4 probes...
Tracing Julia GC Stop-The-World Latency... Hit Ctrl-C to end.
^C


@usecs[1743412]:
[4, 8)               971 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@|
[8, 16)              837 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@        |
[16, 32)             129 |@@@@@@                                              |
[32, 64)              10 |                                                    |
[64, 128)              1 |                                                    |
```

우리는 실행된 줄리아 프로세스에서 스톱-더-월드 단계의 지연 분포를 볼 수 있습니다.

### Task spawn monitor

작업이 다른 작업을 생성할 때를 아는 것은 때때로 유용합니다. 이는 `rt__new__task`를 사용하면 매우 쉽게 확인할 수 있습니다. 프로브의 첫 번째 인수인 `parent`는 새 작업을 생성하는 기존 작업입니다. 이는 모니터링하려는 작업의 주소를 알고 있다면, 해당 특정 작업이 생성한 작업들을 쉽게 확인할 수 있음을 의미합니다. 이를 수행하는 방법을 살펴보겠습니다. 먼저 Julia 세션을 시작하고 PID와 REPL의 작업 주소를 가져옵니다:

```
> julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825

2> current_task()
Task (runnable) @0x00007f524d088010
```

이제 `bpftrace`를 시작하고 이 부모에 대해서만 `rt__new__task`를 모니터링할 수 있습니다:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("작업: %x\n", arg0); }'`

(위에서 `arg0`는 첫 번째 인수, `parent`입니다).

단일 작업을 생성하면:

`@async 1+1`

이 작업이 생성되는 것을 봅니다:

`작업: 4d088010`

그러나 새로 생성된 작업에서 여러 작업을 생성하면:

```julia
@async for i in 1:10
   @async 1+1
end
```

우리는 여전히 `bpftrace`에서 하나의 작업만 보고 있습니다:

`작업: 4d088010`

그리고 여전히 우리가 모니터링하고 있는 동일한 작업입니다! 물론, 이 필터를 제거하여 *모든* 새로 생성된 작업을 쉽게 볼 수 있습니다:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("작업: %x\n", arg0); }'`

```
Task: 4d088010
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
```

우리는 우리의 루트 작업과 새로 생성된 작업이 열 개의 더 새로운 작업의 부모 역할을 하는 것을 볼 수 있습니다.

### Thundering herd detection

작업 런타임은 종종 "우르르 몰려드는 무리" 문제로 고통받을 수 있습니다. 조용한 작업 런타임에 작업이 추가되면, 각 스레드가 처리할 작업이 충분하지 않더라도 모든 스레드가 잠에서 깨어날 수 있습니다. 이로 인해 모든 스레드가 깨어나는 동안 추가적인 지연과 CPU 사이클이 발생할 수 있으며, 동시에 실행할 작업을 찾지 못해 다시 잠에 빠질 수 있습니다.

이 문제는 `bpftrace`를 사용하여 쉽게 설명할 수 있습니다. 먼저, 한 터미널에서 여러 스레드(이 예에서는 6개)를 사용하여 Julia를 시작하고 해당 프로세스의 PID를 가져옵니다:

```
> julia -t 6
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825
```

그리고 다른 터미널에서 `bpftrace`를 시작하여 우리의 프로세스를 모니터링하고, 특히 `rt__sleep__check__wake` 훅을 프로빙합니다:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("스레드가 깨어났습니다! %x\n", arg0); }'`

이제 우리는 Julia에서 단일 작업을 생성하고 실행합니다:

`Threads.@spawn 1+1`

그리고 `bpftrace`에서 다음과 같은 내용이 출력되는 것을 볼 수 있습니다:

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

비록 우리가 단일 작업만 생성했지만 (이 작업은 한 번에 하나의 스레드만 처리할 수 있습니다), 우리는 다른 모든 스레드를 깨웠습니다! 미래에는 더 스마트한 작업 런타임이 단일 스레드만 깨우거나 아예 깨우지 않을 수도 있습니다 (생성하는 스레드가 이 작업을 실행할 수 있습니다!), 그리고 우리는 이러한 행동이 사라지는 것을 보아야 합니다.

### Task Monitor with BPFnative.jl

BPFnative.jl은 `bpftrace`와 마찬가지로 USDT 프로브 포인트에 연결할 수 있습니다. 작업 런타임, GC 및 스레드 수면/깨우기 전환을 모니터링하기 위한 데모가 제공됩니다: [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl).

## Notes on using `bpftrace`

bpftrace 형식의 예제 프로브는 다음과 같습니다:

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

프로브 선언은 `usdt` 종류를 취하며, 그 다음에는 라이브러리의 경로 또는 PID, 제공자 이름 `julia` 및 프로브 이름 `gc__begin`이 옵니다. `libjulia-internal.so`에 대한 상대 경로를 사용하고 있지만, 이는 프로덕션 시스템에서는 절대 경로일 필요가 있을 수 있습니다.

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)
