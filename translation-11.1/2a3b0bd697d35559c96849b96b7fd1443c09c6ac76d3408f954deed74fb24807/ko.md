# [Asynchronous Programming](@id man-asynchronous)

프로그램이 외부 세계와 상호작용해야 할 때, 예를 들어 인터넷을 통해 다른 기계와 통신할 때, 프로그램 내의 작업이 예측할 수 없는 순서로 발생해야 할 수 있습니다. 예를 들어, 프로그램이 파일을 다운로드해야 한다고 가정해 보겠습니다. 우리는 다운로드 작업을 시작하고, 다운로드가 완료될 때까지 기다리는 동안 다른 작업을 수행한 다음, 다운로드된 파일이 사용 가능할 때 필요한 코드를 다시 실행하고 싶습니다. 이러한 시나리오는 비동기 프로그래밍의 영역에 해당하며, 개념적으로 여러 작업이 동시에 발생하기 때문에 때때로 동시 프로그래밍이라고도 합니다.

이러한 시나리오를 해결하기 위해 Julia는 [`Task`](@ref)(대칭 코루틴, 경량 스레드, 협력적 다중 작업 또는 일회성 계속으로도 알려짐) 을 제공합니다. 컴퓨팅 작업의 일부(실제로는 특정 함수를 실행하는 것)가 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`로 지정되면, 다른 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`로 전환하여 이를 중단할 수 있습니다. 원래의 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`는 나중에 다시 시작할 수 있으며, 이 시점에서 중단된 지점부터 다시 시작됩니다. 처음에는 이것이 함수 호출과 유사하게 보일 수 있습니다. 그러나 두 가지 주요 차이점이 있습니다. 첫째, 작업 전환은 어떤 공간도 사용하지 않으므로 호출 스택을 소모하지 않고도 무수히 많은 작업 전환이 발생할 수 있습니다. 둘째, 작업 간 전환은 어떤 순서로든 발생할 수 있지만, 함수 호출에서는 호출된 함수가 실행을 마쳐야 제어가 호출 함수로 돌아옵니다.

## Basic `Task` operations

`Task`는 수행할 계산 작업의 핸들로 생각할 수 있습니다. 그것은 생성-시작-실행-완료 생애 주기를 가지고 있습니다. 작업은 실행할 0-인수 함수에서 `Task` 생성자를 호출하거나 [`@task`](@ref) 매크로를 사용하여 생성됩니다:

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x`는 `Task(()->x)`와 같습니다.

이 작업은 5초 동안 대기한 후 `done`을 출력합니다. 그러나 아직 실행되지 않았습니다. 준비가 되면 [`schedule`](@ref)를 호출하여 실행할 수 있습니다:

```julia-repl
julia> schedule(t);
```

REPL에서 이것을 시도하면 `schedule`이 즉시 반환되는 것을 볼 수 있습니다. 이는 단순히 `t`를 실행할 작업의 내부 큐에 추가하기 때문입니다. 그런 다음 REPL은 다음 프롬프트를 인쇄하고 추가 입력을 기다립니다. 키보드 입력을 기다리는 동안 다른 작업이 실행될 기회를 제공하므로 그 시점에서 `t`가 시작됩니다. `t`는 [`sleep`](@ref)를 호출하여 타이머를 설정하고 실행을 중지합니다. 다른 작업이 예약되어 있다면 그때 실행될 수 있습니다. 5초 후, 타이머가 작동하고 `t`를 재시작하며 `done`이 인쇄되는 것을 볼 수 있습니다. 그 후 `t`는 완료됩니다.

[`wait`](@ref) 함수는 다른 작업이 완료될 때까지 호출 작업을 차단합니다. 예를 들어, 만약 당신이 입력하면

```julia-repl
julia> schedule(t); wait(t)
```

대신 `schedule`만 호출하는 것이 아니라, 다음 입력 프롬프트가 나타나기 전에 5초의 일시 정지가 있습니다. 이는 REPL이 진행하기 전에 `t`가 완료되기를 기다리고 있기 때문입니다.

작업을 생성하고 즉시 예약하고 싶어하는 것은 일반적이므로, 이를 위해 매크로 [`@async`](@ref)가 제공됩니다 –- `@async x`는 `schedule(@task x)`와 동일합니다.

## Communicating with Channels

일부 문제에서는 필요한 작업의 다양한 조각이 함수 호출로 자연스럽게 연결되지 않습니다. 수행해야 할 작업 중에서 명확한 "호출자"나 "피호출자"가 없습니다. 예를 들어, 생산자-소비자 문제에서는 하나의 복잡한 절차가 값을 생성하고 다른 복잡한 절차가 이를 소비합니다. 소비자는 값을 얻기 위해 단순히 생산자 함수를 호출할 수 없는데, 이는 생산자가 더 많은 값을 생성해야 할 수도 있고 아직 반환할 준비가 되어 있지 않을 수 있기 때문입니다. 작업을 사용하면 생산자와 소비자가 필요에 따라 계속 실행할 수 있으며, 필요에 따라 값을 주고받을 수 있습니다.

줄리아는 이 문제를 해결하기 위해 [`Channel`](@ref) 메커니즘을 제공합니다. `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`는 여러 작업이 읽고 쓸 수 있는 대기 가능한 선입선출 큐입니다.

생산자 작업을 정의해 보겠습니다. 이 작업은 [`put!`](@ref) 호출을 통해 값을 생성합니다. 값을 소비하기 위해서는 생산자가 새로운 작업에서 실행되도록 예약해야 합니다. 1-인수 함수를 인수로 받아들이는 특별한 [`Channel`](@ref) 생성자를 사용하여 채널에 바인딩된 작업을 실행할 수 있습니다. 그런 다음 채널 객체에서 값을 반복적으로 [`take!`](@ref) 할 수 있습니다:

```jldoctest producer
julia> function producer(c::Channel)
           put!(c, "start")
           for n=1:4
               put!(c, 2n)
           end
           put!(c, "stop")
       end;

julia> chnl = Channel(producer);

julia> take!(chnl)
"start"

julia> take!(chnl)
2

julia> take!(chnl)
4

julia> take!(chnl)
6

julia> take!(chnl)
8

julia> take!(chnl)
"stop"
```

이 행동을 생각하는 한 가지 방법은 `producer`가 여러 번 반환할 수 있었다는 것입니다. [`put!`](@ref)에 대한 호출 사이에서 프로듀서의 실행이 중단되고 소비자가 제어권을 가지게 됩니다.

반환된 [`Channel`](@ref)는 `for` 루프에서 반복 가능한 객체로 사용될 수 있으며, 이 경우 루프 변수는 생성된 모든 값을 취합니다. 채널이 닫히면 루프가 종료됩니다.

```jldoctest producer
julia> for x in Channel(producer)
           println(x)
       end
start
2
4
6
8
stop
```

생산자에서 채널을 명시적으로 닫을 필요가 없다는 점에 유의하세요. 이는 [`Channel`](@ref)를 [`Task`](@ref)에 바인딩하는 행위가 채널의 열린 수명을 바인딩된 작업의 수명과 연결하기 때문입니다. 작업이 종료되면 채널 객체는 자동으로 닫힙니다. 여러 채널을 작업에 바인딩할 수 있으며, 그 반대도 가능합니다.

[`Task`](@ref) 생성자는 0개의 인수를 받는 함수를 기대하는 반면, [`Channel`](@ref) 메서드는 단일 인수 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`를 받는 함수를 기대합니다. 일반적인 패턴은 생산자가 매개변수화되는 경우로, 이 경우 0개 또는 1개의 인수를 받는 [anonymous function](@ref man-anonymous-functions)를 생성하기 위해 부분 함수 적용이 필요합니다.

[`Task`](@ref) 객체에 대해서는 직접적으로 또는 편리한 매크로를 사용하여 수행할 수 있습니다:

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

더욱 고급 작업 분배 패턴을 조정하기 위해, [`bind`](@ref) 및 [`schedule`](@ref)는 [`Task`](@ref) 및 [`Channel`](@ref) 생성자와 함께 사용되어 채널 집합을 생산자/소비자 작업 집합에 명시적으로 연결할 수 있습니다.

### More on Channels

채널은 파이프처럼 시각화할 수 있습니다. 즉, 쓰기 끝과 읽기 끝이 있습니다:

  * 여러 작가가 서로 다른 작업에서 [`put!`](@ref) 호출을 통해 동시에 같은 채널에 쓸 수 있습니다.
  * 다양한 작업에서 여러 리더가 [`take!`](@ref) 호출을 통해 데이터를 동시에 읽을 수 있습니다.
  * 예시로:

    ```julia
    # Given Channels c1 and c2,
    c1 = Channel(32)
    c2 = Channel(32)

    # and a function `foo` which reads items from c1, processes the item read
    # and writes a result to c2,
    function foo()
        while true
            data = take!(c1)
            [...]               # process data
            put!(c2, result)    # write out result
        end
    end

    # we can schedule `n` instances of `foo` to be active concurrently.
    for _ in 1:n
        errormonitor(@async foo())
    end
    ```
  * 채널은 `Channel{T}(sz)` 생성자를 통해 생성됩니다. 채널은 오직 `T` 유형의 객체만 보유할 수 있습니다. 유형이 지정되지 않으면 채널은 모든 유형의 객체를 보유할 수 있습니다. `sz`는 채널이 언제든지 보유할 수 있는 최대 요소 수를 나타냅니다. 예를 들어, `Channel(32)`는 최대 32개의 임의 유형의 객체를 보유할 수 있는 채널을 생성합니다. `Channel{MyType}(64)`는 언제든지 최대 64개의 `MyType` 객체를 보유할 수 있습니다.
  * 만약 [`Channel`](@ref)가 비어 있다면, 독자들은 ([`take!`](@ref) 호출 시) 데이터가 사용 가능해질 때까지 차단됩니다.
  * 만약 a [`Channel`](@ref) 가 가득 차면, 작가들은 (a [`put!`](@ref) 호출에서) 공간이 생길 때까지 차단됩니다.
  * [`isready`](@ref)는 채널에 어떤 객체가 있는지 확인하고, [`wait`](@ref)는 객체가 사용 가능해질 때까지 기다립니다.
  * [`Channel`](@ref)는 처음에 열린 상태입니다. 이는 [`take!`](@ref) 및 [`put!`](@ref) 호출을 통해 자유롭게 읽고 쓸 수 있음을 의미합니다. [`close`](@ref)는 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`를 닫습니다. 닫힌 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`에서 `4d61726b646f776e2e436f64652822222c2022707574212229_40726566`는 실패합니다. 예를 들어:

    ```julia-repl
    julia> c = Channel(2);

    julia> put!(c, 1) # `put!` on an open channel succeeds
    1

    julia> close(c);

    julia> put!(c, 2) # `put!` on a closed channel throws an exception.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```
  * [`take!`](@ref) 및 [`fetch`](@ref) (값을 제거하지 않고 검색함) 는 닫힌 채널에서 기존 값을 성공적으로 반환하며, 값이 비워질 때까지 계속됩니다. 위의 예를 계속하면:

    ```julia-repl
    julia> fetch(c) # Any number of `fetch` calls succeed.
    1

    julia> fetch(c)
    1

    julia> take!(c) # The first `take!` removes the value.
    1

    julia> take!(c) # No more data available on a closed channel.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```

간단한 예제를 고려해 보겠습니다. 여기서는 작업 간 통신을 위해 채널을 사용하는 방법을 보여줍니다. 우리는 단일 `jobs` 채널에서 데이터를 처리하기 위해 4개의 작업을 시작합니다. 작업은 `job_id`로 식별되며, 채널에 기록됩니다. 이 시뮬레이션의 각 작업은 `job_id`를 읽고, 무작위 시간만큼 대기한 후, `job_id`와 시뮬레이션된 시간을 튜플로 결과 채널에 다시 기록합니다. 마지막으로 모든 `results`가 출력됩니다.

```julia-repl
julia> const jobs = Channel{Int}(32);

julia> const results = Channel{Tuple}(32);

julia> function do_work()
           for job_id in jobs
               exec_time = rand()
               sleep(exec_time)                # simulates elapsed time doing actual work
                                               # typically performed externally.
               put!(results, (job_id, exec_time))
           end
       end;

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for i in 1:4 # start 4 tasks to process requests in parallel
           errormonitor(@async do_work())
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds")
           global n = n - 1
       end
4 finished in 0.22 seconds
3 finished in 0.45 seconds
1 finished in 0.5 seconds
7 finished in 0.14 seconds
2 finished in 0.78 seconds
5 finished in 0.9 seconds
9 finished in 0.36 seconds
6 finished in 0.87 seconds
8 finished in 0.79 seconds
10 finished in 0.64 seconds
12 finished in 0.5 seconds
11 finished in 0.97 seconds
0.029772311
```

`errormonitor(t)` 대신에, 더 강력한 솔루션은 `bind(results, t)`를 사용하는 것입니다. 이는 예상치 못한 실패를 기록할 뿐만 아니라, 관련 리소스를 닫고 예외를 모든 곳으로 전파하도록 강제합니다.

## More task operations

작업 작업은 [`yieldto`](@ref)라는 저수준 원시 작업을 기반으로 구축됩니다. `yieldto(task, value)`는 현재 작업을 일시 중지하고 지정된 `task`로 전환하며, 해당 작업의 마지막 `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` 호출이 지정된 `value`를 반환하도록 합니다. `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`는 작업 스타일 제어 흐름을 사용하기 위해 필요한 유일한 작업입니다. 호출하고 반환하는 대신 항상 다른 작업으로 전환하고 있습니다. 이것이 이 기능이 "대칭 코루틴"이라고도 불리는 이유입니다. 각 작업은 동일한 메커니즘을 사용하여 전환됩니다.

[`yieldto`](@ref)는 강력하지만, 작업의 대부분은 이를 직접 호출하지 않습니다. 그 이유를 고려해 보십시오. 현재 작업에서 벗어나면 언젠가는 다시 돌아가고 싶겠지만, 언제 돌아가야 할지, 어떤 작업이 돌아가는 책임을 지는지 아는 것은 상당한 조정이 필요할 수 있습니다. 예를 들어, [`put!`](@ref)와 [`take!`](@ref)는 차단 작업으로, 채널의 맥락에서 사용될 때 소비자가 누구인지 기억하기 위해 상태를 유지합니다. 소비 작업을 수동으로 추적할 필요가 없다는 점이 `4d61726b646f776e2e436f64652822222c2022707574212229_40726566`를 저수준의 `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`보다 사용하기 쉽게 만듭니다.

[`yieldto`](@ref) 외에도 작업을 효과적으로 사용하기 위해 몇 가지 기본 기능이 필요합니다.

  * [`current_task`](@ref)는 현재 실행 중인 작업에 대한 참조를 가져옵니다.
  * [`istaskdone`](@ref)는 작업이 종료되었는지 여부를 쿼리합니다.
  * [`istaskstarted`](@ref)는 작업이 실행되었는지 여부를 쿼리합니다.
  * [`task_local_storage`](@ref)는 현재 작업에 특정한 키-값 저장소를 조작합니다.

## Tasks and events

대부분의 작업 전환은 I/O 요청과 같은 이벤트를 기다리는 결과로 발생하며, Julia Base에 포함된 스케줄러에 의해 수행됩니다. 스케줄러는 실행 가능한 작업의 큐를 유지하고, 메시지 도착과 같은 외부 이벤트에 따라 작업을 재시작하는 이벤트 루프를 실행합니다.

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

모든 경우에 [`wait`](@ref)는 궁극적으로 작업을 큐에 추가하고 재시작하는 역할을 하는 [`Condition`](@ref) 객체에서 작동합니다. 작업이 `4d61726b646f776e2e436f64652822222c2022776169742229_40726566`를 `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566`에서 호출하면, 해당 작업은 실행 불가능으로 표시되고 조건의 큐에 추가되며 스케줄러로 전환됩니다. 스케줄러는 다른 작업을 실행하거나 외부 이벤트를 기다리며 차단됩니다. 모든 것이 잘 진행되면, 결국 이벤트 핸들러가 조건에서 [`notify`](@ref)를 호출하여 해당 조건을 기다리는 작업이 다시 실행 가능해지게 합니다.

명시적으로 [`Task`](@ref)를 호출하여 생성된 작업은 처음에 스케줄러에 알려지지 않습니다. 이를 통해 원하실 경우 [`yieldto`](@ref)를 사용하여 작업을 수동으로 관리할 수 있습니다. 그러나 이러한 작업이 이벤트를 기다릴 때, 이벤트가 발생하면 여전히 자동으로 재시작됩니다.
