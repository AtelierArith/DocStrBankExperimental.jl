```
Threads.@threads [schedule] for ... end
```

병렬로 `for` 루프를 실행하는 매크로입니다. 반복 공간은 거칠게 분할된 작업에 분배됩니다. 이 정책은 `schedule` 인수로 지정할 수 있습니다. 루프의 실행은 모든 반복의 평가를 기다립니다.

참고: [`@spawn`](@ref Threads.@spawn) 및 [`Distributed`](@ref man-distributed)의 `pmap`.

# 확장 도움말

## 의미론

스케줄링 옵션에 의해 더 강력한 보장이 지정되지 않는 한, `@threads` 매크로에 의해 실행되는 루프는 다음과 같은 의미론을 가집니다.

`@threads` 매크로는 루프 본문을 불특정한 순서로 잠재적으로 동시에 실행합니다. 작업과 작업자 스레드의 정확한 할당을 지정하지 않습니다. 할당은 각 실행마다 다를 수 있습니다. 루프 본문 코드(그로부터 전이적으로 호출되는 모든 코드를 포함)는 반복이 작업에 분배되는 방식이나 실행되는 작업자 스레드에 대한 가정을 해서는 안 됩니다. 각 반복의 루프 본문은 다른 반복과 독립적으로 진행할 수 있어야 하며 데이터 경쟁으로부터 자유로워야 합니다. 따라서 반복 간의 잘못된 동기화는 교착 상태를 초래할 수 있으며, 동기화되지 않은 메모리 접근은 정의되지 않은 동작을 초래할 수 있습니다.

예를 들어, 위의 조건은 다음을 의미합니다:

  * 반복에서 획득한 잠금은 반드시 같은 반복 내에서 해제되어야 합니다.
  * `Channel`과 같은 차단 원시를 사용하여 반복 간에 통신하는 것은 잘못된 것입니다.
  * 반복 간에 공유되지 않는 위치에만 쓰기(잠금 또는 원자적 작업이 사용되지 않는 한).
  * `:static` 스케줄이 사용되지 않는 한, [`threadid()`](@ref Threads.threadid)의 값은 단일 반복 내에서도 변경될 수 있습니다. [`Task Migration`](@ref man-task-migration)을 참조하십시오.

## 스케줄러

스케줄러 인수가 없으면 정확한 스케줄링은 지정되지 않으며 Julia 릴리스에 따라 다릅니다. 현재는 스케줄러가 지정되지 않은 경우 `:dynamic`이 사용됩니다.

!!! compat "Julia 1.5"
    `schedule` 인수는 Julia 1.5부터 사용할 수 있습니다.


### `:dynamic` (기본값)

`:dynamic` 스케줄러는 사용 가능한 작업자 스레드에 대해 반복을 동적으로 실행합니다. 현재 구현은 각 반복의 작업 부하가 균일하다고 가정합니다. 그러나 이 가정은 미래에 제거될 수 있습니다.

이 스케줄링 옵션은 기본 실행 메커니즘에 대한 힌트일 뿐입니다. 그러나 몇 가지 속성을 기대할 수 있습니다. `:dynamic` 스케줄러가 사용하는 `Task`의 수는 사용 가능한 작업자 스레드의 수의 작은 상수 배수로 제한됩니다 ([`Threads.threadpoolsize()`](@ref)). 각 작업은 반복 공간의 인접한 영역을 처리합니다. 따라서 `@threads :dynamic for x in xs; f(x); end`는 일반적으로 `@sync for x in xs; @spawn f(x); end`보다 더 효율적입니다. 여기서 `length(xs)`는 작업자 스레드의 수보다 훨씬 크고 `f(x)`의 실행 시간은 작업을 생성하고 동기화하는 비용보다 상대적으로 작습니다(일반적으로 10마이크로초 미만).

!!! compat "Julia 1.8"
    `schedule` 인수에 대한 `:dynamic` 옵션은 Julia 1.8부터 사용 가능하며 기본값입니다.


### `:greedy`

`:greedy` 스케줄러는 최대 [`Threads.threadpoolsize()`](@ref) 작업을 생성하며, 각 작업은 생성되는 주어진 반복 값에 대해 탐욕적으로 작업합니다. 하나의 작업이 작업을 마치면 다음 값을 반복자에서 가져옵니다. 개별 작업이 수행하는 작업은 반복자에서 인접한 값에 대해 반드시 수행되는 것은 아닙니다. 주어진 반복자는 영원히 값을 생성할 수 있으며, 반복자 인터페이스만 필요합니다(인덱싱 없음).

이 스케줄링 옵션은 일반적으로 개별 반복의 작업 부하가 균일하지 않거나 큰 분포를 가질 때 좋은 선택입니다.

!!! compat "Julia 1.11"
    `schedule` 인수에 대한 `:greedy` 옵션은 Julia 1.11부터 사용 가능합니다.


### `:static`

`:static` 스케줄러는 각 스레드당 하나의 작업을 생성하고 반복을 균등하게 나누어 각 작업을 특정 스레드에 할당합니다. 특히, [`threadid()`](@ref Threads.threadid)의 값은 하나의 반복 내에서 일정하다고 보장됩니다. 다른 `@threads` 루프 내에서 사용하거나 1이 아닌 스레드에서 사용하면 `:static`을 지정하는 것은 오류입니다.

!!! note
    `:static` 스케줄링은 Julia 1.3 이전에 작성된 코드의 전환을 지원하기 위해 존재합니다. 새로 작성된 라이브러리 함수에서는 이 옵션을 사용하는 것이 권장되지 않습니다. 이 옵션을 사용하는 함수는 임의의 작업자 스레드에서 호출할 수 없습니다.


## 예제

다양한 스케줄링 전략을 설명하기 위해, 주어진 초 수 동안 실행되는 비양보 타이머 루프를 포함하는 다음 함수 `busywait`를 고려하십시오.

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 seconds (16.33 k allocations: 899.255 KiB, 0.25% compilation time)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 seconds (16.05 k allocations: 883.919 KiB, 0.66% compilation time)
```

`:dynamic` 예제는 2초가 걸리며, 비어 있는 스레드 중 하나가 1초 반복 두 개를 실행하여 for 루프를 완료할 수 있습니다. ```
