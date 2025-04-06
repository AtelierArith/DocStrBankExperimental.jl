```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> collection
```

컬렉션 `c`를 변환하여 각 요소에 `f`를 적용합니다. 사용 가능한 작업자와 작업을 사용합니다.

여러 컬렉션 인수가 있는 경우, `f`를 요소별로 적용합니다.

`f`는 모든 작업자 프로세스에서 사용할 수 있어야 합니다. 자세한 내용은 [코드 가용성 및 패키지 로딩](@ref code-availability)을 참조하십시오.

작업자 풀이 지정되지 않은 경우, 모든 사용 가능한 작업자가 [`CachingPool`](@ref)을 통해 사용됩니다.

기본적으로 `pmap`은 지정된 모든 작업자에게 계산을 분산합니다. 로컬 프로세스만 사용하고 작업에 분산하려면 `distributed=false`를 지정하십시오. 이는 [`asyncmap`](@ref)을 사용하는 것과 동일합니다. 예를 들어, `pmap(f, c; distributed=false)`는 `asyncmap(f,c; ntasks=()->nworkers())`와 동일합니다.

`pmap`은 `batch_size` 인수를 통해 프로세스와 작업의 혼합을 사용할 수도 있습니다. 배치 크기가 1보다 큰 경우, 컬렉션은 여러 배치로 처리되며, 각 배치의 길이는 `batch_size` 이하입니다. 배치는 자유로운 작업자에게 단일 요청으로 전송되며, 로컬 [`asyncmap`](@ref)이 여러 동시 작업을 사용하여 배치의 요소를 처리합니다.

오류가 발생하면 `pmap`은 컬렉션의 나머지 부분을 처리하지 않습니다. 이 동작을 재정의하려면, 단일 인수(즉, 예외)를 받는 오류 처리 함수를 `on_error` 인수로 지정할 수 있습니다. 이 함수는 오류를 다시 발생시켜 처리를 중단하거나, 계속 진행하기 위해 어떤 값을 반환하여 결과와 함께 호출자에게 반환할 수 있습니다.

다음 두 가지 예를 고려하십시오. 첫 번째 예는 예외 객체를 인라인으로 반환하고, 두 번째 예는 예외 대신 0을 반환합니다:

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

오류는 실패한 계산을 재시도하여 처리할 수도 있습니다. 키워드 인수 `retry_delays`와 `retry_check`는 각각 [`retry`](@ref)로 키워드 인수 `delays`와 `check`로 전달됩니다. 배치가 지정된 경우, 전체 배치가 실패하면 배치의 모든 항목이 재시도됩니다.

`on_error`와 `retry_delays`가 모두 지정된 경우, 재시도하기 전에 `on_error` 후크가 호출됩니다. `on_error`가 예외를 던지지 않거나 다시 발생시키지 않으면 해당 요소는 재시도되지 않습니다.

예: 오류가 발생할 경우, 요소에 대해 최대 3회 지연 없이 `f`를 재시도합니다.

```julia
pmap(f, c; retry_delays = zeros(3))
```

예: 예외가 [`InexactError`](@ref) 유형이 아닐 경우에만 `f`를 재시도하며, 최대 3회까지 지수적으로 증가하는 지연을 사용합니다. 모든 `InexactError` 발생에 대해 `NaN`을 반환합니다.

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```
