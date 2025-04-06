# [Multi-Threading](@id man-multithreading)

이 [blog post](https://julialang.org/blog/2019/07/multithreading/)를 방문하여 Julia의 다중 스레딩 기능에 대한 프레젠테이션을 확인하세요.

## Starting Julia with multiple threads

기본적으로, Julia는 단일 실행 스레드로 시작됩니다. 이는 [`Threads.nthreads()`](@ref) 명령어를 사용하여 확인할 수 있습니다:

```jldoctest
julia> Threads.nthreads()
1
```

실행 스레드의 수는 `-t`/`--threads` 명령줄 인수를 사용하거나 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 환경 변수를 사용하여 제어됩니다. 두 가지 모두 지정된 경우 `-t`/`--threads`가 우선합니다.

스레드 수는 정수(`--threads=4`)로 지정하거나 `auto`(`--threads=auto`)로 지정할 수 있으며, 여기서 `auto`는 사용할 유용한 기본 스레드 수를 추론하려고 시도합니다(자세한 내용은 [Command-line Options](@ref command-line-interface)를 참조하십시오).

!!! compat "Julia 1.5"
    `-t`/`--threads` 명령줄 인수는 최소한 Julia 1.5가 필요합니다. 이전 버전에서는 대신 환경 변수를 사용해야 합니다.


!!! compat "Julia 1.7"
    `auto`를 환경 변수 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS)의 값으로 사용하는 것은 최소한 Julia 1.7이 필요합니다. 이전 버전에서는 이 값이 무시됩니다.


Julia를 4개의 스레드로 시작합시다:

```bash
$ julia --threads 4
```

우리가 사용할 수 있는 스레드가 4개인지 확인해 봅시다.

```julia-repl
julia> Threads.nthreads()
4
```

하지만 우리는 현재 마스터 스레드에 있습니다. 확인하기 위해 우리는 함수 [`Threads.threadid`](@ref)를 사용합니다.

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    환경 변수를 사용하려면 Bash (Linux/macOS)에서 다음과 같이 설정할 수 있습니다:

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C 셸은 Linux/macOS에서, CMD는 Windows에서:

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    Windows에서 PowerShell:

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    이것은 Julia를 시작하기 *전에* 수행해야 합니다.


!!! note
    `-t`/`--threads`로 지정된 스레드 수는 `-p`/`--procs` 또는 `--machine-file` 명령줄 옵션을 사용하여 생성된 작업자 프로세스에 전파됩니다. 예를 들어, `julia -p2 -t2`는 2개의 작업자 프로세스가 있는 1개의 메인 프로세스를 생성하며, 이 세 프로세스 모두 2개의 스레드가 활성화되어 있습니다. 작업자 스레드에 대한 보다 세밀한 제어를 위해 [`addprocs`](@ref)를 사용하고 `-t`/`--threads`를 `exeflags`로 전달하십시오.


### Multiple GC Threads

가비지 컬렉터(GC)는 여러 스레드를 사용할 수 있습니다. 사용되는 스레드의 수는 컴퓨트 작업자 스레드 수의 절반이거나 `--gcthreads` 명령줄 인수 또는 [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS) 환경 변수를 사용하여 구성됩니다.

!!! compat "Julia 1.10"
    `--gcthreads` 명령줄 인수는 최소한 Julia 1.10이 필요합니다.


## [Threadpools](@id man-threadpools)

프로그램의 스레드가 실행할 많은 작업으로 바쁠 때, 작업은 지연을 경험할 수 있으며 이는 프로그램의 반응성과 상호작용성에 부정적인 영향을 미칠 수 있습니다. 이를 해결하기 위해, 작업이 상호작용적임을 지정할 수 있습니다 [`Threads.@spawn`](@ref) 할 때:

```julia
using Base.Threads
@spawn :interactive f()
```

인터랙티브 작업은 높은 대기 시간 작업을 피해야 하며, 긴 지속 시간 작업인 경우 자주 양보해야 합니다.

Julia는 대화형 작업을 실행하기 위해 하나 이상의 스레드를 예약하여 시작할 수 있습니다:

```bash
$ julia --threads 3,1
```

환경 변수 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS)도 유사하게 사용할 수 있습니다:

```bash
export JULIA_NUM_THREADS=3,1
```

이것은 `:default` 스레드 풀에서 3개의 스레드와 `:interactive` 스레드 풀에서 1개의 스레드를 사용하여 Julia를 시작합니다:

```julia-repl
julia> using Base.Threads

julia> nthreadpools()
2

julia> threadpool() # the main thread is in the interactive thread pool
:interactive

julia> nthreads(:default)
3

julia> nthreads(:interactive)
1

julia> nthreads()
3
```

!!! note
    `nthreads`의 인수가 없는 버전은 기본 풀의 스레드 수를 반환합니다.


!!! note
    줄리아가 인터랙티브 스레드로 시작되었는지에 따라, 메인 스레드는 기본 스레드 풀 또는 인터랙티브 스레드 풀에 있습니다.


숫자 중 하나 또는 둘 다 `auto`라는 단어로 대체될 수 있으며, 이는 Julia가 합리적인 기본값을 선택하도록 합니다.

## The `@threads` Macro

간단한 예제를 원주율 스레드를 사용하여 작업해 봅시다. 제로로 구성된 배열을 생성해 보겠습니다:

```jldoctest
julia> a = zeros(10)
10-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
```

이 배열에 4개의 스레드를 사용하여 동시에 작업을 수행합시다. 각 스레드는 자신의 스레드 ID를 각 위치에 기록합니다.

Julia는 [`Threads.@threads`](@ref) 매크로를 사용하여 병렬 루프를 지원합니다. 이 매크로는 `for` 루프 앞에 붙여져 루프가 다중 스레드 영역임을 Julia에 알립니다:

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

반복 공간은 스레드 간에 분할되며, 이후 각 스레드는 자신의 스레드 ID를 할당된 위치에 기록합니다:

```julia-repl
julia> a
10-element Vector{Float64}:
 1.0
 1.0
 1.0
 2.0
 2.0
 2.0
 3.0
 3.0
 4.0
 4.0
```

[`Threads.@threads`](@ref)는 [`@distributed`](@ref)와 같은 선택적 축소 매개변수가 없습니다.

### Using `@threads` without data-races

데이터 레이스의 개념은 ["Communication and data races between threads"](@ref man-communication-and-data-races)에서 자세히 설명되어 있습니다. 현재로서는 데이터 레이스가 잘못된 결과와 위험한 오류를 초래할 수 있다는 것만 알고 계시면 됩니다.

`sum_single` 함수를 멀티스레드로 만들고 싶다고 가정해 봅시다.

```julia-repl
julia> function sum_single(a)
           s = 0
           for i in a
               s += i
           end
           s
       end
sum_single (generic function with 1 method)

julia> sum_single(1:1_000_000)
500000500000
```

단순히 `@threads`를 추가하면 여러 스레드가 동시에 `s`를 읽고 쓰면서 데이터 경합이 발생합니다.

```julia-repl
julia> function sum_multi_bad(a)
           s = 0
           Threads.@threads for i in a
               s += i
           end
           s
       end
sum_multi_bad (generic function with 1 method)

julia> sum_multi_bad(1:1_000_000)
70140554652
```

결과가 `500000500000`이 아니라는 점에 유의하세요. 이는 예상되는 결과이며, 각 평가마다 변경될 가능성이 높습니다.

이 문제를 해결하기 위해, 작업에 특화된 버퍼를 사용하여 합계를 경쟁이 없는 청크로 분할할 수 있습니다. 여기서 `sum_single`은 자체 내부 버퍼 `s`와 함께 재사용됩니다. 입력 벡터 `a`는 병렬 작업을 위해 `nthreads()` 청크로 나뉩니다. 그런 다음 `Threads.@spawn`을 사용하여 각 청크를 개별적으로 합산하는 작업을 생성합니다. 마지막으로, 각 작업의 결과를 다시 `sum_single`을 사용하여 합산합니다:

```julia-repl
julia> function sum_multi_good(a)
           chunks = Iterators.partition(a, length(a) ÷ Threads.nthreads())
           tasks = map(chunks) do chunk
               Threads.@spawn sum_single(chunk)
           end
           chunk_sums = fetch.(tasks)
           return sum_single(chunk_sums)
       end
sum_multi_good (generic function with 1 method)

julia> sum_multi_good(1:1_000_000)
500000500000
```

!!! note
    버퍼는 `threadid()`를 기반으로 관리해서는 안 됩니다. 즉, `buffers = zeros(Threads.nthreads())`와 같이 하면 안 됩니다. 왜냐하면 동시 작업이 양보할 수 있기 때문에 여러 동시 작업이 주어진 스레드에서 동일한 버퍼를 사용할 수 있어 데이터 경합의 위험이 발생할 수 있습니다. 또한, 스레드가 두 개 이상 사용 가능한 경우 작업이 양보 지점에서 스레드를 변경할 수 있으며, 이는 [task migration](@ref man-task-migration)로 알려져 있습니다.


또 다른 옵션은 작업/스레드 간에 공유되는 변수에 대한 원자적 작업을 사용하는 것입니다. 이는 작업의 특성에 따라 더 성능이 좋을 수 있습니다.

## [Communication and data-races between threads](@id man-communication-and-data-races)

줄리아의 스레드는 공유 메모리를 통해 통신할 수 있지만, 올바르고 데이터 경합이 없는 다중 스레드 코드를 작성하는 것은 notoriously 어렵습니다. 줄리아의 [`Channel`](@ref)는 스레드 안전하며 안전하게 통신하는 데 사용할 수 있습니다. 아래에는 데이터 경합을 피하기 위해 [locks](@ref man-using-locks)와 [atomics](@ref man-atomic-operations)를 사용하는 방법에 대한 섹션도 있습니다.

### Data-race freedom

당신의 프로그램이 데이터 레이스가 없도록 보장하는 것은 전적으로 당신의 책임이며, 이 요구 사항을 준수하지 않는 경우 여기서 약속된 것은 아무것도 가정할 수 없습니다. 관찰된 결과는 매우 직관적이지 않을 수 있습니다.

데이터 경합이 발생하면 Julia는 메모리 안전하지 않습니다. **다른 스레드가 데이터를 쓸 수 있는 경우 *모든* 데이터를 읽는 것에 매우 주의해야 하며, 이는 세그멘테이션 오류나 그보다 더 심각한 결과를 초래할 수 있습니다**. 아래는 서로 다른 스레드에서 전역 변수에 접근하는 몇 가지 안전하지 않은 방법입니다:

```julia
Thread 1:
global b = false
global a = rand()
global b = true

Thread 2:
while !b; end
bad_read1(a) # it is NOT safe to access `a` here!

Thread 3:
while !@isdefined(a); end
bad_read2(a) # it is NOT safe to access `a` here
```

### [Using locks to avoid data-races](@id man-using-locks)

데이터 경합을 피하고 스레드 안전 코드를 작성하기 위한 중요한 도구는 "잠금"의 개념입니다. 잠금은 잠글 수 있고 잠금을 해제할 수 있습니다. 만약 스레드가 잠금을 잠그고 해제하지 않았다면, 그 스레드는 잠금을 "보유"하고 있다고 말합니다. 잠금이 하나만 있을 경우, 잠금을 보유해야 데이터를 접근하는 코드를 작성하면 여러 스레드가 동시에 동일한 데이터에 접근하지 않도록 보장할 수 있습니다. 잠금과 변수 간의 연결은 프로그래머에 의해 이루어지며, 프로그램에 의해 이루어지지 않는다는 점에 유의해야 합니다.

예를 들어, `my_lock`이라는 잠금을 생성하고, 변수 `my_variable`을 변경하는 동안 잠금을 걸 수 있습니다. 이는 `@lock` 매크로를 사용하여 가장 간단하게 수행됩니다:

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

유사한 패턴을 사용하여 동일한 잠금과 변수를 사용하되 다른 스레드에서 작업을 수행하면 데이터 경합이 발생하지 않습니다.

우리는 다음 두 가지 방법으로 `lock`의 함수형 버전을 사용하여 위의 작업을 수행할 수 있었습니다:

```julia-repl
julia> lock(my_lock) do
           my_variable[1] = 100
       end
100

julia> begin
           lock(my_lock)
           try
               my_variable[1] = 100
           finally
               unlock(my_lock)
           end
       end
100
```

세 가지 옵션은 모두 동등합니다. 최종 버전이 항상 잠금이 해제되도록 보장하기 위해 명시적인 `try`-블록을 요구하는 반면, 처음 두 버전은 이를 내부적으로 처리한다는 점에 유의하십시오. 다른 스레드에서 접근하는 데이터(예: 전역 변수나 클로저 변수에 할당)를 변경할 때는 항상 위의 잠금 패턴을 사용해야 합니다. 이를 소홀히 하면 예기치 않은 심각한 결과를 초래할 수 있습니다.

### [Atomic Operations](@id man-atomic-operations)

줄리아는 값을 *원자적으로* 접근하고 수정하는 것을 지원합니다. 즉, 스레드 안전한 방식으로 [race conditions](https://en.wikipedia.org/wiki/Race_condition)을 피할 수 있습니다. 값(원시 타입이어야 함)은 [`Threads.Atomic`](@ref)로 래핑되어야 이 방식으로 접근해야 함을 나타냅니다. 여기 예시를 볼 수 있습니다:

```julia-repl
julia> i = Threads.Atomic{Int}(0);

julia> ids = zeros(4);

julia> old_is = zeros(4);

julia> Threads.@threads for id in 1:4
           old_is[id] = Threads.atomic_add!(i, id)
           ids[id] = id
       end

julia> old_is
4-element Vector{Float64}:
 0.0
 1.0
 7.0
 3.0

julia> i[]
 10

julia> ids
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

우리가 원자 태그 없이 덧셈을 시도했다면, 경쟁 조건으로 인해 잘못된 답을 얻었을 수 있습니다. 경쟁을 피하지 않았다면 발생할 수 있는 예:

```julia-repl
julia> using Base.Threads

julia> Threads.nthreads()
4

julia> acc = Ref(0)
Base.RefValue{Int64}(0)

julia> @threads for i in 1:1000
          acc[] += 1
       end

julia> acc[]
926

julia> acc = Atomic{Int64}(0)
Atomic{Int64}(0)

julia> @threads for i in 1:1000
          atomic_add!(acc, 1)
       end

julia> acc[]
1000
```

#### [Per-field atomics](@id man-atomics)

우리는 [`@atomic`](@ref Base.@atomic), [`@atomicswap`](@ref Base.@atomicswap), [`@atomicreplace`](@ref Base.@atomicreplace) 매크로와 [`@atomiconce`](@ref Base.@atomiconce) 매크로를 사용하여 더 세분화된 수준에서 원자성을 사용할 수 있습니다.

메모리 모델의 구체적인 세부 사항 및 디자인의 기타 세부 사항은 [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0)에 작성되어 있으며, 이는 나중에 공식적으로 발표될 예정입니다.

구조체 선언의 어떤 필드든 `@atomic`으로 장식할 수 있으며, 이후 모든 쓰기는 `@atomic`으로 표시되어야 하고, 정의된 원자적 순서 중 하나(`:monotonic`, `:acquire`, `:release`, `:acquire_release`, 또는 `:sequentially_consistent`)를 사용해야 합니다. 원자적 필드의 모든 읽기는 원자적 순서 제약으로 주석을 달 수 있으며, 지정하지 않으면 단조(완화) 순서로 수행됩니다.

!!! compat "Julia 1.7"
    Per-field atomics는 최소한 Julia 1.7이 필요합니다.


## Side effects and mutable function arguments

멀티 스레딩을 사용할 때는 [pure](https://en.wikipedia.org/wiki/Pure_function)가 아닌 함수를 사용할 때 주의해야 합니다. 잘못된 결과를 얻을 수 있기 때문입니다. 예를 들어, [name ending with `!`](@ref bang-convention)을 가진 함수는 관례적으로 인수를 수정하므로 순수하지 않습니다.

## @threadcall

외부 라이브러리, 예를 들어 [`ccall`](@ref)를 통해 호출되는 라이브러리는 Julia의 작업 기반 I/O 메커니즘에 문제를 일으킵니다. C 라이브러리가 블로킹 작업을 수행하면, 호출이 반환될 때까지 Julia 스케줄러가 다른 작업을 실행할 수 없습니다. (예외적으로, Julia로 다시 호출하는 사용자 정의 C 코드에 대한 호출은 양보할 수 있으며, `jl_yield()`를 호출하는 C 코드도 포함됩니다. 이는 [`yield`](@ref)의 C 동등물입니다.)

[`@threadcall`](@ref) 매크로는 이러한 시나리오에서 실행이 지연되는 것을 피할 수 있는 방법을 제공합니다. 이는 별도의 스레드에서 실행할 C 함수를 예약합니다. 기본 크기가 4인 스레드 풀을 사용합니다. 스레드 풀의 크기는 환경 변수 `UV_THREADPOOL_SIZE`를 통해 제어됩니다. 무료 스레드를 기다리는 동안, 그리고 스레드가 사용 가능해지면 함수 실행 중에 요청된 작업(주요 Julia 이벤트 루프에서)은 다른 작업에 양보합니다. `@threadcall`은 실행이 완료될 때까지 반환되지 않음을 유의하십시오. 사용자 관점에서 볼 때, 이는 다른 Julia API와 마찬가지로 차단 호출입니다.

호출된 함수가 Julia로 다시 호출하지 않는 것이 매우 중요합니다. 그렇지 않으면 세그멘테이션 오류가 발생합니다.

`@threadcall`는 향후 Julia 버전에서 제거되거나 변경될 수 있습니다.

## Caveats

현재, Julia 런타임 및 표준 라이브러리의 대부분의 작업은 사용자 코드가 데이터 경합이 없는 경우 스레드 안전한 방식으로 사용할 수 있습니다. 그러나 일부 영역에서는 스레드 지원을 안정화하기 위한 작업이 진행 중입니다. 다중 스레드 프로그래밍은 많은 고유한 어려움이 있으며, 스레드를 사용하는 프로그램이 비정상적이거나 바람직하지 않은 동작(예: 충돌 또는 불가사의한 결과)을 보일 경우, 일반적으로 스레드 상호작용이 먼저 의심되어야 합니다.

Julia에서 스레드를 사용할 때 알아야 할 몇 가지 특정 제한 사항과 경고가 있습니다:

  * 기본 컬렉션 유형은 여러 스레드가 동시에 사용하고 그 중 적어도 하나의 스레드가 컬렉션을 수정하는 경우 수동 잠금이 필요합니다(일반적인 예로는 배열의 `push!` 또는 `Dict`에 항목을 삽입하는 것이 있습니다).
  * [`@spawn`](@ref Threads.@spawn)에서 사용되는 일정은 비결정적이며 신뢰할 수 없습니다.
  * 계산 집약적이고 메모리 할당을 하지 않는 작업은 메모리를 할당하는 다른 스레드에서 가비지 수집이 실행되는 것을 방해할 수 있습니다. 이러한 경우 `GC.safepoint()`에 대한 수동 호출을 삽입하여 가비지 수집이 실행될 수 있도록 해야 할 수 있습니다. 이 제한은 미래에 제거될 것입니다.
  * 최상위 작업, 예를 들어 `include` 또는 타입, 메서드 및 모듈 정의의 `eval`을 병렬로 실행하는 것을 피하십시오.
  * 라이브러리에 의해 등록된 파이널라이저는 스레드가 활성화되면 작동하지 않을 수 있습니다. 이는 스레딩이 자신 있게 널리 채택되기 전에 생태계 전반에 걸쳐 일부 전환 작업이 필요할 수 있음을 의미합니다. 추가 세부정보는 [the safe use of finalizers](@ref man-finalizers) 섹션을 참조하십시오.

## [Task Migration](@id man-task-migration)

작업이 특정 스레드에서 실행되기 시작한 후 작업이 양보하면 다른 스레드로 이동할 수 있습니다.

이러한 작업은 [`@spawn`](@ref Threads.@spawn) 또는 [`@threads`](@ref Threads.@threads)으로 시작되었을 수 있지만, `@threads`의 `:static` 스케줄 옵션은 threadid를 고정합니다.

이는 대부분의 경우 [`threadid()`](@ref Threads.threadid)가 작업 내에서 상수로 취급되어서는 안 되며, 따라서 버퍼 또는 상태 객체의 벡터에 인덱싱하는 데 사용되어서는 안 된다는 것을 의미합니다.

!!! compat "Julia 1.7"
    작업 마이그레이션은 Julia 1.7에서 도입되었습니다. 이전에는 작업이 시작된 동일한 스레드에 항상 남아 있었습니다.


## [Safe use of Finalizers](@id man-finalizers)

파이널라이저는 어떤 코드든 중단할 수 있기 때문에, 전역 상태와 상호작용하는 방식에 매우 주의해야 합니다. 불행히도, 파이널라이저가 사용되는 주된 이유는 전역 상태를 업데이트하기 위해서입니다(순수 함수는 일반적으로 파이널라이저로서 그다지 의미가 없습니다). 이는 우리를 약간의 딜레마로 이끕니다. 이 문제를 해결하기 위한 몇 가지 접근 방식이 있습니다:

1. 단일 스레드일 때, 코드는 내부 `jl_gc_enable_finalizers` C 함수를 호출하여 중요한 영역 내에서 파이널라이저가 예약되는 것을 방지할 수 있습니다. 내부적으로, 이는 특정 작업(증분 패키지 로딩, 코드 생성 등)을 수행할 때 재귀를 방지하기 위해 일부 함수(예: C 잠금) 내에서 사용됩니다. 잠금과 이 플래그의 조합을 사용하면 파이널라이저를 안전하게 만들 수 있습니다.
2. 두 번째 전략은 Base에서 몇 군데 사용되며, 최종화기를 명시적으로 지연시켜 비재귀적으로 잠금을 획득할 수 있을 때까지 기다리는 것입니다. 다음 예시는 이 전략이 `Distributed.finalize_ref`에 어떻게 적용될 수 있는지를 보여줍니다:

    ```julia
    function finalize_ref(r::AbstractRemoteRef)
        if r.where > 0 # Check if the finalizer is already run
            if islocked(client_refs) || !trylock(client_refs)
                # delay finalizer for later if we aren't free to acquire the lock
                finalizer(finalize_ref, r)
                return nothing
            end
            try # `lock` should always be followed by `try`
                if r.where > 0 # Must check again here
                    # Do actual cleanup here
                    r.where = 0
                end
            finally
                unlock(client_refs)
            end
        end
        nothing
    end
    ```
3. 관련된 세 번째 전략은 수익 없는 큐를 사용하는 것입니다. 현재 Base에는 락이 없는 큐가 구현되어 있지 않지만, `Base.IntrusiveLinkedListSynchronized{T}`가 적합합니다. 이 전략은 이벤트 루프가 있는 코드에 자주 좋은 전략이 될 수 있습니다. 예를 들어, 이 전략은 `Gtk.jl`에서 생명 주기 참조 카운팅을 관리하는 데 사용됩니다. 이 접근 방식에서는 `finalizer` 내부에서 명시적인 작업을 수행하지 않고, 대신 더 안전한 시간에 실행하기 위해 큐에 추가합니다. 사실, Julia의 작업 스케줄러는 이미 이를 사용하므로, `finalizer`를 `x -> @spawn do_cleanup(x)`로 정의하는 것이 이 접근 방식의 한 예입니다. 그러나 이 방법은 `do_cleanup`이 실행되는 스레드를 제어하지 않으므로, `do_cleanup`은 여전히 락을 획득해야 합니다. 자신의 큐를 구현하면 이 필요는 없으며, 명시적으로 자신의 스레드에서만 해당 큐를 비울 수 있습니다.
