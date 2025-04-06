# Multi-processing and Distributed Computing

모듈 [`Distributed`](@ref man-distributed)는 Julia와 함께 제공되는 표준 라이브러리의 일부로 분산 메모리 병렬 컴퓨팅의 구현을 제공합니다.

대부분의 현대 컴퓨터는 하나 이상의 CPU를 가지고 있으며, 여러 컴퓨터를 클러스터로 결합할 수 있습니다. 이러한 여러 CPU의 힘을 활용하면 많은 계산을 더 빠르게 완료할 수 있습니다. 성능에 영향을 미치는 두 가지 주요 요소가 있습니다: CPU 자체의 속도와 메모리에 대한 접근 속도입니다. 클러스터에서는 특정 CPU가 동일한 컴퓨터(노드) 내의 RAM에 가장 빠르게 접근할 수 있다는 것이 꽤 명확합니다. 아마도 더 놀라운 것은, 일반적인 멀티코어 노트북에서도 메인 메모리의 속도와 [cache](https://www.akkadia.org/drepper/cpumemory.pdf)의 속도 차이로 인해 유사한 문제가 발생한다는 것입니다. 따라서 좋은 멀티프로세싱 환경은 특정 CPU가 메모리의 일부에 대한 "소유권"을 제어할 수 있도록 해야 합니다. Julia는 메시지 전달을 기반으로 한 멀티프로세싱 환경을 제공하여 프로그램이 여러 프로세스에서 별도의 메모리 도메인에서 동시에 실행될 수 있도록 합니다.

줄리아의 메시지 전달 구현은 MPI[^1]와 같은 다른 환경과 다릅니다. 줄리아에서의 통신은 일반적으로 "단방향"이며, 이는 프로그래머가 두 프로세스 작업에서 오직 하나의 프로세스만 명시적으로 관리해야 함을 의미합니다. 또한 이러한 작업은 일반적으로 "메시지 전송" 및 "메시지 수신"처럼 보이지 않고, 사용자 함수 호출과 같은 더 높은 수준의 작업을 닮아 있습니다.

줄리아에서 분산 프로그래밍은 두 가지 기본 요소인 *원격 참조*와 *원격 호출*에 기반합니다. 원격 참조는 특정 프로세스에 저장된 객체를 참조하기 위해 모든 프로세스에서 사용할 수 있는 객체입니다. 원격 호출은 한 프로세스가 다른(가능하면 동일한) 프로세스에서 특정 인수로 특정 함수를 호출하도록 요청하는 것입니다.

원격 참조는 두 가지 유형이 있습니다: [`Future`](@ref Distributed.Future) 및 [`RemoteChannel`](@ref).

원격 호출은 결과로 [`Future`](@ref Distributed.Future)를 반환합니다. 원격 호출은 즉시 반환되며, 호출을 수행한 프로세스는 원격 호출이 다른 곳에서 발생하는 동안 다음 작업으로 진행됩니다. [`wait`](@ref)를 호출하여 원격 호출이 완료될 때까지 기다릴 수 있으며, 반환된 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`를 사용하여 결과의 전체 값을 얻을 수 있습니다. [`fetch`](@ref)를 사용합니다.

반면에, [`RemoteChannel`](@ref)는 재작성 가능하다. 예를 들어, 여러 프로세스가 동일한 원격 `Channel`을 참조하여 처리 작업을 조정할 수 있다.

각 프로세스에는 관련된 식별자가 있습니다. 대화형 Julia 프롬프트를 제공하는 프로세스는 항상 `id`가 1입니다. 기본적으로 병렬 작업에 사용되는 프로세스는 "작업자"라고 합니다. 프로세스가 하나만 있을 때, 프로세스 1은 작업자로 간주됩니다. 그렇지 않으면 작업자는 프로세스 1을 제외한 모든 프로세스로 간주됩니다. 결과적으로, [`pmap`](@ref)와 같은 병렬 처리 방법의 이점을 얻으려면 2개 이상의 프로세스를 추가해야 합니다. 단일 프로세스를 추가하는 것은 긴 계산이 작업자에서 실행되는 동안 주 프로세스에서 다른 작업을 수행하려는 경우 유용합니다.

`julia -p n`는 로컬 머신에서 `n` 개의 작업자 프로세스를 제공합니다. 일반적으로 `n`은 머신의 CPU 스레드(논리 코어) 수와 같아야 합니다. `-p` 인수는 암묵적으로 모듈 [`Distributed`](@ref man-distributed)를 로드합니다.

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

[`remotecall`](@ref)에 대한 첫 번째 인수는 호출할 함수입니다. Julia의 대부분의 병렬 프로그래밍은 특정 프로세스나 사용 가능한 프로세스 수를 참조하지 않지만, `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566`는 더 세밀한 제어를 제공하는 저수준 인터페이스로 간주됩니다. `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566`에 대한 두 번째 인수는 작업을 수행할 프로세스의 `id`이며, 나머지 인수는 호출되는 함수에 전달됩니다.

첫 번째 줄에서 프로세스 2에게 2x2 랜덤 행렬을 생성하도록 요청했고, 두 번째 줄에서는 그에 1을 더하도록 요청했습니다. 두 계산의 결과는 두 개의 미래인 `r`과 `s`에서 확인할 수 있습니다. [`@spawnat`](@ref) 매크로는 첫 번째 인수로 지정된 프로세스에서 두 번째 인수의 표현식을 평가합니다.

가끔 원격으로 계산된 값을 즉시 원할 수 있습니다. 이는 일반적으로 원격 객체에서 데이터를 읽어 다음 로컬 작업에 필요한 데이터를 얻을 때 발생합니다. [`remotecall_fetch`](@ref) 함수가 이 목적을 위해 존재합니다. 이는 `fetch(remotecall(...))`와 동등하지만 더 효율적입니다.

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

이것은 작업자 2에서 배열을 가져오고 첫 번째 값을 반환합니다. `fetch`는 이 경우 배열을 소유한 작업자에서 실행되므로 데이터를 이동하지 않는다는 점에 유의하세요. 다음과 같이 작성할 수도 있습니다:

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

[`getindex(r,1,1)`](@ref)는 [equivalent](@ref man-array-indexing)에서 `r[1,1]`로 변환되므로, 이 호출은 미래의 `r`의 첫 번째 요소를 가져옵니다.

작업을 수행할 위치를 선택하는 `:any` 기호를 [`@spawnat`](@ref)에 전달할 수 있습니다.

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

`1 .+ fetch(r)` 대신 `1 .+ r`을 사용했다는 점에 유의하세요. 이는 코드가 어디에서 실행될지 모르기 때문입니다. 일반적으로 [`fetch`](@ref)가 `r`을 덧셈을 수행하는 프로세스로 이동하는 데 필요할 수 있습니다. 이 경우, [`@spawnat`](@ref)는 `r`을 소유한 프로세스에서 계산을 수행할 만큼 똑똑하므로 `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`는 no-op(작업이 수행되지 않음)입니다.

(다음과 같은 [`@spawnat`](@ref)는 내장된 것이 아니라 Julia에서 [macro](@ref man-macros)로 정의된 것입니다. 이러한 구조를 직접 정의하는 것도 가능합니다.)

중요한 점은, 한 번 가져오면 [`Future`](@ref Distributed.Future)가 로컬에 값을 캐시한다는 것입니다. 이후의 [`fetch`](@ref) 호출은 네트워크 홉을 수반하지 않습니다. 모든 참조하는 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`가 가져오면, 원격 저장 값은 삭제됩니다.

[`@async`](@ref)는 [`@spawnat`](@ref)와 유사하지만, 로컬 프로세스에서만 작업을 실행합니다. 우리는 각 프로세스에 대해 "피더" 작업을 생성하는 데 사용합니다. 각 작업은 계산해야 할 다음 인덱스를 선택한 다음, 해당 프로세스가 완료될 때까지 기다리고, 인덱스가 소진될 때까지 반복합니다. 피더 작업은 메인 작업이 [`@sync`](@ref) 블록의 끝에 도달할 때까지 실행을 시작하지 않으며, 이 시점에서 제어를 포기하고 모든 로컬 작업이 완료될 때까지 기다린 후 함수에서 반환합니다. v0.7 이상에서는 피더 작업이 모두 동일한 프로세스에서 실행되기 때문에 `nextidx`를 통해 상태를 공유할 수 있습니다. `Tasks`가 협력적으로 예약되더라도, [asynchronous I/O](@ref faq-async-io)와 같은 일부 맥락에서는 여전히 잠금이 필요할 수 있습니다. 이는 컨텍스트 전환이 잘 정의된 지점에서만 발생함을 의미합니다: 이 경우 [`remotecall_fetch`](@ref)가 호출될 때입니다. 이것은 현재 구현 상태이며, 향후 Julia 버전에서 변경될 수 있습니다. 이는 최대 N `Tasks`를 M `Process`에서 실행할 수 있도록 하는 것을 목표로 합니다. 즉, [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models)입니다. 그런 다음 `nextidx`에 대한 잠금 획득/해제 모델이 필요할 것이며, 여러 프로세스가 동시에 리소스를 읽고 쓸 수 있도록 허용하는 것은 안전하지 않습니다.

## [Code Availability and Loading Packages](@id code-availability)

당신의 코드는 이를 실행하는 모든 프로세스에서 사용할 수 있어야 합니다. 예를 들어, 다음을 줄리아 프롬프트에 입력하세요:

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

프로세스 1은 `rand2` 함수에 대해 알고 있었지만, 프로세스 2는 알지 못했다.

가장 일반적으로 파일이나 패키지에서 코드를 로드하게 되며, 어떤 프로세스가 코드를 로드할지 제어하는 데 상당한 유연성이 있습니다. 다음 코드를 포함하는 파일 `DummyModule.jl`을 고려해 보십시오:

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

모든 프로세스에서 `MyType`을 참조하기 위해서는 `DummyModule.jl`을 모든 프로세스에서 로드해야 합니다. `include("DummyModule.jl")`를 호출하면 단일 프로세스에서만 로드됩니다. 모든 프로세스에서 로드하려면 [`@everywhere`](@ref) 매크로를 사용하세요 (Julia를 `julia -p 2`로 시작합니다):

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

일반적으로, 이것은 어떤 프로세스에서도 `DummyModule`을 범위에 포함시키지 않으며, 이는 [`using`](@ref) 또는 [`import`](@ref)를 요구합니다. 게다가, 한 프로세스에서 `DummyModule`이 범위에 포함되면, 다른 프로세스에서는 포함되지 않습니다:

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

그러나 여전히 `DummyModule`이 범위에 없더라도 `MyType`을 로드한 프로세스에 보낼 수 있는 가능성이 있습니다:

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

파일은 또한 시작 시 `-L` 플래그를 사용하여 여러 프로세스에서 미리 로드될 수 있으며, 드라이버 스크립트를 사용하여 계산을 수행할 수 있습니다:

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

위 예제에서 드라이버 스크립트를 실행하는 Julia 프로세스의 `id`는 1로, 대화형 프롬프트를 제공하는 프로세스와 같습니다.

마지막으로, `DummyModule.jl`이 독립 실행 파일이 아니라 패키지인 경우, `using DummyModule`은 모든 프로세스에서 `DummyModule.jl`을 *로드*하지만, [`using`](@ref)가 호출된 프로세스에서만 범위에 가져옵니다.

## Starting and managing worker processes

기본 Julia 설치는 두 가지 유형의 클러스터에 대한 내장 지원을 제공합니다:

  * 위에 표시된 대로 `-p` 옵션으로 지정된 로컬 클러스터.
  * `--machine-file` 옵션을 사용하여 머신을 가로지르는 클러스터. 이는 비밀번호 없는 `ssh` 로그인을 사용하여 지정된 머신에서 Julia 작업자 프로세스를 시작합니다(현재 호스트와 동일한 경로에서). 각 머신 정의는 `[count*][user@]host[:port] [bind_addr[:port]]` 형식을 따릅니다. `user`는 현재 사용자로 기본 설정되며, `port`는 표준 ssh 포트로 기본 설정됩니다. `count`는 노드에서 생성할 작업자의 수이며 기본값은 1입니다. 선택적 `bind-to bind_addr[:port]`는 다른 작업자가 이 작업자에 연결하는 데 사용할 IP 주소와 포트를 지정합니다.

!!! note
    줄리아는 일반적으로 이전 버전과의 호환성을 추구하지만, 작업자 프로세스에 코드를 배포하는 것은 [`Serialization.serialize`](@ref)에 의존합니다. 해당 문서에서 지적했듯이, 이는 서로 다른 줄리아 버전 간에 작동할 것이라고 보장할 수 없으므로, 모든 머신의 모든 작업자가 동일한 버전을 사용하는 것이 권장됩니다.


함수 [`addprocs`](@ref), [`rmprocs`](@ref), [`workers`](@ref) 및 기타 함수는 클러스터에서 프로세스를 추가, 제거 및 쿼리하는 프로그래밍 수단으로 사용할 수 있습니다.

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

모듈 [`Distributed`](@ref man-distributed)는 [`addprocs`](@ref)를 호출하기 전에 마스터 프로세스에서 명시적으로 로드되어야 합니다. 이 모듈은 워커 프로세스에서 자동으로 사용 가능합니다.

!!! note
    작업자는 `~/.julia/config/startup.jl` 시작 스크립트를 실행하지 않으며, 다른 실행 중인 프로세스와 전역 상태(예: 명령줄 스위치, 전역 변수, 새로운 메서드 정의 및 로드된 모듈)를 동기화하지 않습니다. 특정 환경으로 작업자를 초기화하려면 `addprocs(exeflags="--project")`를 사용할 수 있으며, 그 후에 `@everywhere using <modulename>` 또는 `@everywhere include("file.jl")`를 사용할 수 있습니다.


다른 유형의 클러스터는 아래의 [ClusterManagers](@ref) 섹션에 설명된 대로 사용자 정의 `ClusterManager`를 작성하여 지원할 수 있습니다.

## Data Movement

메시지를 전송하고 데이터를 이동하는 것은 분산 프로그램에서 대부분의 오버헤드를 차지합니다. 메시지 수와 전송되는 데이터 양을 줄이는 것은 성능과 확장성을 달성하는 데 중요합니다. 이를 위해서는 줄리아의 다양한 분산 프로그래밍 구성 요소가 수행하는 데이터 이동을 이해하는 것이 중요합니다.

[`fetch`](@ref)는 객체를 로컬 머신으로 이동하라는 직접적인 요청이므로 명시적인 데이터 이동 작업으로 간주될 수 있습니다. [`@spawnat`](@ref) (및 몇 가지 관련 구성 요소)도 데이터를 이동하지만, 이는 그리 명확하지 않으므로 암시적인 데이터 이동 작업이라고 할 수 있습니다. 무작위 행렬을 구성하고 제곱하는 두 가지 접근 방식을 고려해 보십시오:

방법 1:

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

방법 2:

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

차이는 사소해 보이지만, 실제로는 [`@spawnat`](@ref)의 동작 때문에 상당히 중요합니다. 첫 번째 방법에서는 무작위 행렬이 로컬에서 구성된 다음, 제곱을 위해 다른 프로세스로 전송됩니다. 두 번째 방법에서는 무작위 행렬이 다른 프로세스에서 구성되고 제곱됩니다. 따라서 두 번째 방법은 첫 번째 방법보다 훨씬 적은 데이터를 전송합니다.

이 장난감 예제에서는 두 가지 방법을 쉽게 구별하고 선택할 수 있습니다. 그러나 실제 프로그램에서는 데이터 이동을 설계하는 데 더 많은 고민과 측정이 필요할 수 있습니다. 예를 들어, 첫 번째 프로세스가 행렬 `A`가 필요하다면 첫 번째 방법이 더 나을 수 있습니다. 또는 `A`를 계산하는 것이 비용이 많이 들고 현재 프로세스만 가지고 있다면, 다른 프로세스로 이동하는 것은 피할 수 없을 것입니다. 또는 현재 프로세스가 [`@spawnat`](@ref)와 `fetch(Bref)` 사이에 할 일이 거의 없다면, 병렬성을 완전히 없애는 것이 더 나을 수 있습니다. 또는 `rand(1000,1000)`이 더 비싼 작업으로 대체된다고 상상해 보십시오. 그러면 이 단계만을 위해 또 다른 `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566` 문을 추가하는 것이 의미가 있을 수 있습니다.

## Global variables

원격으로 실행된 표현식은 [`@spawnat`](@ref)를 통해, 또는 원격 실행을 위해 지정된 클로저는 [`remotecall`](@ref)를 사용하여 전역 변수를 참조할 수 있습니다. 모듈 `Main` 아래의 전역 바인딩은 다른 모듈의 전역 바인딩과 약간 다르게 처리됩니다. 다음 코드 스니펫을 고려하십시오:

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

이 경우 [`sum`](@ref)는 원격 프로세스에서 정의되어야 합니다. `A`는 로컬 작업 공간에 정의된 전역 변수임을 유의하십시오. 작업자 2는 `Main` 아래에 `A`라는 변수가 없습니다. 클로저 `()->sum(A)`를 작업자 2로 전송하는 행위는 `Main.A`가 2에서 정의되도록 만듭니다. `Main.A`는 호출 [`remotecall_fetch`](@ref)가 반환된 후에도 작업자 2에서 계속 존재합니다. 내장된 전역 참조가 있는 원격 호출(오직 `Main` 모듈 아래에서)은 전역 변수를 다음과 같이 관리합니다:

  * 원격 호출의 일부로 참조되는 경우, 대상 작업자에서 새로운 글로벌 바인딩이 생성됩니다.
  * 전역 상수는 원격 노드에서도 상수로 선언됩니다.
  * 글로벌은 원격 호출의 맥락에서만 대상 작업자에게 다시 전송되며, 그 값이 변경된 경우에만 전송됩니다. 또한 클러스터는 노드 간에 글로벌 바인딩을 동기화하지 않습니다. 예를 들어:

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    위의 코드 조각을 실행하면 작업자 2의 `Main.A` 값이 작업자 3의 `Main.A` 값과 다르게 나타나고, 노드 1의 `Main.A` 값은 `nothing`으로 설정됩니다.

당신이 깨달았듯이, 글로벌과 관련된 메모리는 마스터에서 재할당될 때 수집될 수 있지만, 바인딩이 여전히 유효하기 때문에 워커에서는 그러한 조치가 취해지지 않습니다. [`clear!`](@ref)는 더 이상 필요하지 않을 때 원격 노드에서 특정 글로벌을 `nothing`으로 수동으로 재할당하는 데 사용할 수 있습니다. 이렇게 하면 정기적인 가비지 컬렉션 주기의 일환으로 이들과 관련된 메모리가 해제됩니다.

따라서 프로그램은 원격 호출에서 전역 변수를 참조할 때 주의해야 합니다. 사실, 가능하다면 전역 변수를 아예 피하는 것이 바람직합니다. 전역 변수를 참조해야 한다면, `let` 블록을 사용하여 전역 변수를 지역화하는 것을 고려해 보세요.

예를 들어:

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

보시다시피, 전역 변수 `A`는 작업자 2에서 정의되지만, `B`는 지역 변수로 캡처되므로 작업자 2에서는 `B`에 대한 바인딩이 존재하지 않습니다.

## Parallel Map and Loops

다행히도 많은 유용한 병렬 계산은 데이터 이동을 필요로 하지 않습니다. 일반적인 예로는 몬테카를로 시뮬레이션이 있으며, 여러 프로세스가 독립적인 시뮬레이션 실험을 동시에 처리할 수 있습니다. 우리는 [`@spawnat`](@ref)를 사용하여 두 프로세스에서 동전을 던질 수 있습니다. 먼저, `count_heads.jl`에 다음 함수를 작성하세요:

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

함수 `count_heads`는 단순히 `n`개의 랜덤 비트를 더합니다. 다음은 두 대의 머신에서 몇 가지 실험을 수행하고 결과를 더하는 방법입니다:

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

이 예제는 강력하고 자주 사용되는 병렬 프로그래밍 패턴을 보여줍니다. 여러 프로세스에서 많은 반복이 독립적으로 실행되고, 그 결과는 어떤 함수를 사용하여 결합됩니다. 결합 과정은 일반적으로 텐서 랭크를 줄이기 때문에 *감소(reduction)*라고 불립니다: 숫자의 벡터가 단일 숫자로 줄어들거나, 행렬이 단일 행 또는 열로 줄어드는 등의 방식입니다. 코드에서는 일반적으로 `x = f(x,v[i])` 패턴처럼 보이며, 여기서 `x`는 누산기, `f`는 감소 함수, `v[i]`는 줄어드는 요소입니다. `f`가 결합법칙을 만족하는 것이 바람직하여, 연산이 수행되는 순서가 중요하지 않도록 합니다.

이 패턴을 `count_heads`와 함께 사용하는 것이 일반화될 수 있음을 주목하십시오. 우리는 두 개의 명시적인 [`@spawnat`](@ref) 문을 사용했으며, 이는 병렬성을 두 프로세스로 제한합니다. 임의의 수의 프로세스에서 실행하려면, 분산 메모리에서 실행되는 *병렬 for 루프*를 사용할 수 있으며, 이는 Julia에서 [`@distributed`](@ref)를 사용하여 다음과 같이 작성할 수 있습니다:

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

이 구조는 여러 프로세스에 반복을 할당하고 이를 지정된 축소(이 경우 `(+)`)와 결합하는 패턴을 구현합니다. 각 반복의 결과는 루프 내부의 마지막 표현식의 값으로 취해집니다. 전체 병렬 루프 표현식 자체는 최종 답변으로 평가됩니다.

병렬 for 루프는 직렬 for 루프처럼 보이지만, 그 동작은 극적으로 다릅니다. 특히, 반복은 지정된 순서로 발생하지 않으며, 변수나 배열에 대한 쓰기는 전역적으로 보이지 않습니다. 왜냐하면 반복이 서로 다른 프로세스에서 실행되기 때문입니다. 병렬 루프 내에서 사용되는 모든 변수는 복사되어 각 프로세스에 전송됩니다.

예를 들어, 다음 코드는 의도한 대로 작동하지 않을 것입니다:

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

이 코드는 `a`의 모든 요소를 초기화하지 않습니다. 각 프로세스는 `a`의 별도의 복사본을 가지기 때문입니다. 이러한 병렬 for 루프는 피해야 합니다. 다행히도, [Shared Arrays](@ref man-shared-arrays)를 사용하여 이 제한을 우회할 수 있습니다:

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

"외부" 변수를 병렬 루프에서 사용하는 것은 변수가 읽기 전용인 경우 완전히 합리적입니다:

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

여기 각 반복은 모든 프로세스가 공유하는 벡터 `a`에서 무작위로 선택된 샘플에 `f`를 적용합니다.

보시다시피, 축소 연산자는 필요하지 않은 경우 생략할 수 있습니다. 그런 경우, 루프는 비동기적으로 실행되며, 즉 모든 사용 가능한 작업자에서 독립적인 작업을 생성하고 즉시 [`Future`](@ref Distributed.Future) 배열을 반환합니다. 호출자는 나중에 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 완료를 기다리기 위해 [`fetch`](@ref)를 호출하거나, [`@sync`](@ref)로 접두사를 붙여 루프 끝에서 완료를 기다릴 수 있습니다. 예: `@sync @distributed for`.

일부 경우에는 축소 연산자가 필요하지 않으며, 단순히 특정 범위의 모든 정수(또는 더 일반적으로, 특정 컬렉션의 모든 요소)에 함수를 적용하고자 합니다. 이는 *병렬 맵*이라고 하는 또 다른 유용한 작업으로, Julia에서는 [`pmap`](@ref) 함수로 구현됩니다. 예를 들어, 다음과 같이 여러 개의 큰 랜덤 행렬의 특이값을 병렬로 계산할 수 있습니다:

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

줄리아의 [`pmap`](@ref)는 각 함수 호출이 많은 작업을 수행하는 경우를 위해 설계되었습니다. 반면, `@distributed for`는 각 반복이 작고, 아마도 단순히 두 숫자를 더하는 경우를 처리할 수 있습니다. 병렬 계산을 위해 `4d61726b646f776e2e436f64652822222c2022706d61702229_40726566`와 `@distributed for` 모두 작업자 프로세스만 사용됩니다. `@distributed for`의 경우, 최종 축소는 호출 프로세스에서 수행됩니다.

## Remote References and AbstractChannels

원격 참조는 항상 `AbstractChannel`의 구현을 참조합니다.

`AbstractChannel`의 구체적인 구현체(예: `Channel`)는 [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) 및 [`wait`](@ref)를 구현해야 합니다. [`Future`](@ref Distributed.Future)가 참조하는 원격 객체는 `Channel{Any}(1)`에 저장됩니다. 즉, `Any` 유형의 객체를 보유할 수 있는 크기 1의 `Channel`입니다.

[`RemoteChannel`](@ref)는 재작성 가능하며, 모든 유형 및 크기의 채널이나 `AbstractChannel`의 다른 구현을 가리킬 수 있습니다.

생성자 `RemoteChannel(f::Function, pid)()`는 특정 유형의 여러 값을 보유하는 채널에 대한 참조를 구성할 수 있게 해줍니다. `f`는 `pid`에서 실행되는 함수이며, `AbstractChannel`을 반환해야 합니다.

예를 들어, `RemoteChannel(()->Channel{Int}(10), pid)`는 타입 `Int`와 크기 10인 채널에 대한 참조를 반환합니다. 이 채널은 작업자 `pid`에 존재합니다.

메서드 [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) 및 [`wait`](@ref)는 [`RemoteChannel`](@ref)에서 원격 프로세스의 백업 스토어에 프록시됩니다.

[`RemoteChannel`](@ref)는 사용자 구현 `AbstractChannel` 객체를 참조하는 데 사용할 수 있습니다. 이와 관련된 간단한 예는 원격 저장소로 사전을 사용하는 다음의 `DictChannel`입니다:

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * A [`Channel`](@ref)는 프로세스에 로컬합니다. 워커 2는 워커 3의 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`를 직접 참조할 수 없으며, 그 반대도 마찬가지입니다. 그러나 [`RemoteChannel`](@ref)는 워커 간에 값을 넣고 가져올 수 있습니다.
  * A [`RemoteChannel`](@ref)는 [`Channel`](@ref)에 대한 *핸들*로 생각할 수 있습니다.
  * The process id, `pid`, associated with a [`RemoteChannel`](@ref) identifies the process where the backing store, i.e., the backing [`Channel`](@ref) exists.
  * [`RemoteChannel`](@ref)에 대한 참조가 있는 모든 프로세스는 채널에서 항목을 넣고 가져올 수 있습니다. 데이터는 자동으로 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566`와 연결된 프로세스로 전송(또는 검색)됩니다.
  * [`Channel`](@ref)를 직렬화하면 채널에 있는 모든 데이터도 직렬화됩니다. 따라서 이를 역직렬화하면 원래 객체의 복사본이 생성됩니다.
  * 반면에, [`RemoteChannel`](@ref)의 직렬화는 핸들이 참조하는 [`Channel`](@ref)의 위치와 인스턴스를 식별하는 식별자의 직렬화만 포함됩니다. 따라서 역직렬화된 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` 객체(어떤 작업자에서든)는 원본과 동일한 백업 저장소를 가리킵니다.

위의 채널 예제는 아래와 같이 프로세스 간 통신을 위해 수정될 수 있습니다.

우리는 단일 `jobs` 원격 채널을 처리하기 위해 4명의 작업자를 시작합니다. 작업은 id(`job_id`)로 식별되며, 채널에 작성됩니다. 이 시뮬레이션에서 원격으로 실행되는 각 작업은 `job_id`를 읽고, 무작위 시간 동안 대기한 후, `job_id`, 소요 시간 및 자신의 `pid`를 결과 채널에 튜플로 다시 작성합니다. 마지막으로 모든 `results`가 마스터 프로세스에서 출력됩니다.

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

원격 참조로 언급된 객체는 클러스터 내의 *모든* 보유 참조가 삭제될 때만 해제될 수 있습니다.

값이 저장된 노드는 어떤 작업자가 그것에 대한 참조를 가지고 있는지 추적합니다. 매번 [`RemoteChannel`](@ref) 또는 (가져오지 않은) [`Future`](@ref Distributed.Future)가 작업자에게 직렬화될 때, 참조가 가리키는 노드가 알림을 받습니다. 그리고 매번 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` 또는 (가져오지 않은) `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`가 로컬에서 가비지 수집될 때, 값을 소유한 노드가 다시 알림을 받습니다. 이는 내부 클러스터 인식 직렬 변환기에 구현되어 있습니다. 원격 참조는 실행 중인 클러스터의 맥락에서만 유효합니다. 일반 `IO` 객체에 대한 참조를 직렬화하고 역직렬화하는 것은 지원되지 않습니다.

알림은 "추적" 메시지를 전송하여 수행됩니다. 참조가 다른 프로세스로 직렬화될 때 "참조 추가" 메시지가 전송되고, 참조가 로컬에서 가비지 수집될 때 "참조 삭제" 메시지가 전송됩니다.

[`Future`](@ref Distributed.Future)는 한 번만 쓸 수 있으며 로컬에 캐시됩니다. 따라서 [`fetch`](@ref)하는 행위는 해당 값을 소유한 노드의 참조 추적 정보를 업데이트합니다.

값을 소유한 노드는 해당 값에 대한 모든 참조가 제거되면 이를 해제합니다.

[`Future`](@ref Distributed.Future)를 사용하여 이미 가져온 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`를 다른 노드로 직렬화하면 원래 원격 저장소가 이 시점까지 값을 수집했을 수 있으므로 값도 전송됩니다.

객체가 로컬 가비지 컬렉션되는 *시점*은 객체의 크기와 시스템의 현재 메모리 압력에 따라 달라진다는 점을 주목하는 것이 중요합니다.

원격 참조의 경우, 로컬 참조 객체의 크기는 상당히 작지만, 원격 노드에 저장된 값은 상당히 클 수 있습니다. 로컬 객체가 즉시 수집되지 않을 수 있으므로, [`finalize`](@ref)를 로컬 인스턴스의 [`RemoteChannel`](@ref) 또는 가져오지 않은 [`Future`](@ref Distributed.Future)에 대해 명시적으로 호출하는 것이 좋습니다. [`fetch`](@ref)를 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`에 호출하면 원격 저장소에서 해당 참조가 제거되므로, 가져온 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`에 대해서는 이 작업이 필요하지 않습니다. `4d61726b646f776e2e436f64652822222c202266696e616c697a652229_40726566`를 명시적으로 호출하면 원격 노드에 즉시 메시지가 전송되어 해당 값에 대한 참조를 제거하도록 요청합니다.

한 번 최종화되면 참조는 무효가 되며 이후의 호출에서 사용할 수 없습니다.

## Local invocations

데이터는 실행을 위해 원격 노드로 반드시 복사됩니다. 이는 원격 호출 및 데이터가 다른 노드의 [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future)에 저장될 때 모두 해당됩니다. 예상대로, 이로 인해 원격 노드에 직렬화된 객체의 복사본이 생성됩니다. 그러나 목적지 노드가 로컬 노드인 경우, 즉 호출 프로세스 ID가 원격 노드 ID와 동일한 경우, 이는 로컬 호출로 실행됩니다. 일반적으로 (항상 그렇지는 않지만) 다른 작업에서 실행되지만 데이터의 직렬화/역직렬화는 없습니다. 결과적으로, 호출은 전달된 동일한 객체 인스턴스를 참조하며 복사본이 생성되지 않습니다. 이 동작은 아래에 강조 표시되어 있습니다:

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

보시다시피, [`put!`](@ref)는 로컬 소유의 [`RemoteChannel`](@ref)에서 호출 간에 수정된 동일한 객체 `v`로 인해 저장된 동일한 단일 객체 인스턴스를 결과로 합니다. 반면, `rc`를 소유한 노드가 다른 노드일 경우 `v`의 복사본이 생성됩니다.

일반적으로 이것은 문제가 되지 않는다는 점에 유의해야 합니다. 객체가 로컬에 저장되고 호출 후 수정되는 경우에만 고려해야 할 사항입니다. 이러한 경우 객체의 `deepcopy`를 저장하는 것이 적절할 수 있습니다.

이것은 다음 예에서 볼 수 있듯이 로컬 노드에서의 원격 호출에도 해당됩니다:

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

다시 한 번 볼 수 있듯이, 로컬 노드에 대한 원격 호출은 직접 호출과 동일하게 작동합니다. 호출은 인수로 전달된 로컬 객체를 수정합니다. 원격 호출에서는 인수의 복사본에서 작동합니다.

일반적으로 반복하자면, 이는 문제가 아닙니다. 로컬 노드가 컴퓨트 노드로도 사용되고 있으며, 호출 후 사용되는 인자들이 있다면, 이 동작을 고려해야 하며 필요할 경우 로컬 노드에서 호출된 인자들의 깊은 복사본을 전달해야 합니다. 원격 노드에서의 호출은 항상 인자들의 복사본에서 작동합니다.

## [Shared Arrays](@id man-shared-arrays)

공유 배열은 시스템 공유 메모리를 사용하여 여러 프로세스에서 동일한 배열을 매핑합니다. [`SharedArray`](@ref)는 동일한 머신에서 두 개 이상의 프로세스가 공동으로 접근할 수 있는 대량의 데이터를 원할 때 좋은 선택입니다. 공유 배열 지원은 `SharedArrays` 모듈을 통해 제공되며, 모든 참여 작업자에서 명시적으로 로드해야 합니다.

외부 패키지 [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl)에 의해 보완적인 데이터 구조가 `DArray` 형태로 제공됩니다. [`SharedArray`](@ref)와 유사한 점이 있지만, [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl)의 동작은 상당히 다릅니다. `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`에서는 각 "참여" 프로세스가 전체 배열에 접근할 수 있는 반면, `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c`에서는 각 프로세스가 데이터의 일부에만 로컬 접근할 수 있으며, 두 프로세스가 동일한 청크를 공유하지 않습니다.

[`SharedArray`](@ref) 인덱싱(할당 및 값 접근)은 일반 배열과 마찬가지로 작동하며, 기본 메모리가 로컬 프로세스에 사용 가능하기 때문에 효율적입니다. 따라서 대부분의 알고리즘은 `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`에서 자연스럽게 작동하지만, 단일 프로세스 모드에서 작동합니다. 알고리즘이 [`Array`](@ref) 입력을 고집하는 경우, 기본 배열은 `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`에서 [`sdata`](@ref)를 호출하여 검색할 수 있습니다. 다른 `AbstractArray` 유형의 경우, `4d61726b646f776e2e436f64652822222c202273646174612229_40726566`는 객체 자체를 반환하므로, 모든 `Array` 유형 객체에서 `4d61726b646f776e2e436f64652822222c202273646174612229_40726566`를 안전하게 사용할 수 있습니다.

공유 배열의 생성자는 다음 형식입니다:

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

`N`-차원 비트 타입 `T`와 크기 `dims`의 공유 배열을 `pids`로 지정된 프로세스 간에 생성합니다. 분산 배열과 달리, 공유 배열은 `pids` 명명 인수로 지정된 참여 작업자만 접근할 수 있습니다(같은 호스트에 있는 경우 생성 프로세스도 포함됨). `SharedArray`에서 지원되는 요소는 [`isbits`](@ref)만 가능합니다.

`init` 함수의 시그니처가 `initfn(S::SharedArray)`로 지정되면, 모든 참여 작업자에서 호출됩니다. 각 작업자가 배열의 서로 다른 부분에서 `init` 함수를 실행하도록 지정할 수 있으며, 이를 통해 초기화를 병렬화할 수 있습니다.

여기 간단한 예시입니다:

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref)는 서로 겹치지 않는 일차원 인덱스 범위를 제공하며, 프로세스 간 작업을 나누는 데 때때로 편리합니다. 물론, 원하는 방식으로 작업을 나눌 수 있습니다:

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

모든 프로세스가 기본 데이터에 접근할 수 있으므로, 충돌이 발생하지 않도록 주의해야 합니다. 예를 들어:

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

정의되지 않은 동작을 초래할 수 있습니다. 각 프로세스가 자신의 `pid`로 *전체* 배열을 채우기 때문에, 특정 `S`의 요소에 대해 마지막으로 실행되는 프로세스의 `pid`가 유지됩니다.

보다 확장되고 복잡한 예로, 다음 "커널"을 병렬로 실행하는 것을 고려해 보십시오:

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

이 경우, 1차원 인덱스를 사용하여 작업을 분할하려고 하면 문제가 발생할 가능성이 높습니다. 만약 `q[i,j,t]`가 한 작업자에게 할당된 블록의 끝 근처에 있고 `q[i,j,t+1]`가 다른 작업자에게 할당된 블록의 시작 근처에 있다면, `q[i,j,t]`가 `q[i,j,t+1]`를 계산하는 데 필요한 시점에 준비되지 않을 가능성이 매우 높습니다. 이러한 경우, 배열을 수동으로 청크하는 것이 더 좋습니다. 두 번째 차원을 따라 분할해 보겠습니다. 이 작업자에게 할당된 `(irange, jrange)` 인덱스를 반환하는 함수를 정의합니다:

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

다음으로 커널을 정의합니다:

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

우리는 또한 `SharedArray` 구현을 위한 편리한 래퍼를 정의합니다.

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

이제 단일 프로세스에서 실행되는 세 가지 다른 버전을 비교해 보겠습니다:

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

[`@distributed`](@ref)를 사용하는 하나:

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

그리고 청크로 위임하는 것:

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

`SharedArray`를 생성하고 이 함수들의 시간을 측정하면 다음과 같은 결과를 얻습니다 ( `julia -p 4` 사용):

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

함수를 한 번 실행하여 JIT 컴파일하고 [`@time`](@ref) 두 번째 실행에서 실행하세요:

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

`advection_shared!`의 가장 큰 장점은 작업자 간의 트래픽을 최소화하여 각 작업자가 할당된 작업에 대해 더 오랜 시간 동안 계산할 수 있도록 한다는 점입니다.

### Shared Arrays and Distributed Garbage Collection

원격 참조와 마찬가지로, 공유 배열도 모든 참여 작업자에서 참조를 해제하기 위해 생성 노드의 가비지 수집에 의존합니다. 많은 단기 공유 배열 객체를 생성하는 코드는 가능한 한 빨리 이러한 객체를 명시적으로 종료하는 것에서 이점을 얻을 수 있습니다. 이는 공유 세그먼트를 매핑하는 메모리와 파일 핸들이 더 빨리 해제되는 결과를 가져옵니다.

## ClusterManagers

Julia 프로세스를 논리적 클러스터로 시작하고 관리하며 네트워킹하는 것은 클러스터 관리자를 통해 이루어집니다. `ClusterManager`는 다음에 대한 책임이 있습니다.

  * 클러스터 환경에서 작업자 프로세스 시작하기
  * 각 작업자의 생애 동안 이벤트 관리
  * 선택적으로 데이터 전송 제공

줄리아 클러스터는 다음과 같은 특성을 가지고 있습니다:

  * 초기 Julia 프로세스는 `master`라고도 하며 특별하며 `id`가 1입니다.
  * 오직 `master` 프로세스만 작업자 프로세스를 추가하거나 제거할 수 있습니다.
  * 모든 프로세스는 서로 직접 통신할 수 있습니다.

작업자 간의 연결(내장된 TCP/IP 전송 사용)은 다음과 같은 방식으로 설정됩니다:

  * [`addprocs`](@ref)는 `ClusterManager` 객체와 함께 마스터 프로세스에서 호출됩니다.
  * [`addprocs`](@ref)는 적절한 [`launch`](@ref) 메서드를 호출하여 적절한 머신에서 필요한 수의 작업자 프로세스를 생성합니다.
  * 각 작업자는 무료 포트에서 수신을 시작하고 호스트 및 포트 정보를 [`stdout`](@ref)에 기록합니다.
  * 클러스터 관리자는 각 작업자의 [`stdout`](@ref)를 캡처하여 마스터 프로세스에 제공한다.
  * 마스터 프로세스는 이 정보를 분석하고 각 워커에 대한 TCP/IP 연결을 설정합니다.
  * 모든 작업자는 클러스터 내의 다른 작업자에 대해서도 통지를 받습니다.
  * 각 작업자는 자신의 `id`보다 작은 모든 작업자에게 연결됩니다.
  * 이러한 방식으로 메쉬 네트워크가 구축되며, 모든 작업자는 다른 모든 작업자와 직접 연결됩니다.

기본 전송 계층은 일반 [`TCPSocket`](@ref)을 사용하지만, Julia 클러스터가 자체 전송을 제공하는 것이 가능합니다.

Julia는 두 가지 내장 클러스터 관리자를 제공합니다:

  * `LocalManager`, [`addprocs()`](@ref) 또는 [`addprocs(np::Integer)`](@ref)가 호출될 때 사용됩니다.
  * `SSHManager`, [`addprocs(hostnames::Array)`](@ref)가 호스트 이름 목록과 함께 호출될 때 사용됩니다.

`LocalManager`는 동일한 호스트에서 추가 작업자를 시작하는 데 사용되며, 이를 통해 다중 코어 및 다중 프로세서 하드웨어를 활용합니다.

따라서 최소한의 클러스터 관리자는 다음이 필요합니다:

  * 추상 `ClusterManager`의 하위 유형이 되다
  * [`launch`](@ref)를 구현하여 새로운 작업자를 시작하는 메서드를 작성합니다.
  * [`manage`](@ref)를 구현합니다. 이는 작업자의 생애 동안 다양한 이벤트에서 호출됩니다(예: 인터럽트 신호 전송).

[`addprocs(manager::FooManager)`](@ref addprocs)는 `FooManager`가 구현해야 함:

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

예를 들어, 동일한 호스트에서 작업자를 시작하는 책임이 있는 `LocalManager`가 어떻게 구현되는지 살펴보겠습니다:

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

[`launch`](@ref) 메서드는 다음과 같은 인수를 받습니다:

  * `manager::ClusterManager`: [`addprocs`](@ref)가 호출되는 클러스터 관리자
  * `params::Dict`: [`addprocs`](@ref)에 전달된 모든 키워드 인수
  * `launched::Array`: 하나 이상의 `WorkerConfig` 객체를 추가할 배열
  * `c::Condition`: 작업자가 시작될 때 알림을 받을 조건 변수

[`launch`](@ref) 메서드는 별도의 작업에서 비동기적으로 호출됩니다. 이 작업의 종료는 요청된 모든 작업자가 시작되었음을 신호합니다. 따라서 `4d61726b646f776e2e436f64652822222c20226c61756e63682229_40726566` 함수는 요청된 모든 작업자가 시작되면 즉시 종료되어야 합니다.

새로 시작된 워커들은 서로 및 마스터 프로세스와 모두 연결됩니다. 명령줄 인수 `--worker[=<cookie>]`를 지정하면 시작된 프로세스가 워커로 초기화되고 TCP/IP 소켓을 통해 연결이 설정됩니다.

클러스터의 모든 작업자는 마스터와 동일한 [cookie](@ref man-cluster-cookie)를 공유합니다. 쿠키가 지정되지 않은 경우, 즉 `--worker` 옵션을 사용할 때, 작업자는 표준 입력에서 이를 읽으려고 시도합니다. `LocalManager`와 `SSHManager`는 모두 표준 입력을 통해 새로 시작된 작업자에게 쿠키를 전달합니다.

기본적으로 작업자는 [`getipaddr()`](@ref)에 대한 호출로 반환된 주소의 무료 포트에서 수신 대기합니다. 수신 대기할 특정 주소는 선택적 인수 `--bind-to bind_addr[:port]`로 지정할 수 있습니다. 이는 다중 호스트에 유용합니다.

비 TCP/IP 전송의 예로, 구현은 MPI를 사용할 수 있으며, 이 경우 `--worker`는 지정되어서는 안 됩니다. 대신, 새로 시작된 작업자는 병렬 구조를 사용하기 전에 `init_worker(cookie)`를 호출해야 합니다.

모든 작업자가 시작될 때, [`launch`](@ref) 메서드는 `launched`에 `WorkerConfig` 객체(적절한 필드가 초기화된)를 추가해야 합니다.

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

`WorkerConfig`의 대부분 필드는 내장 관리자에 의해 사용됩니다. 사용자 정의 클러스터 관리자는 일반적으로 `io` 또는 `host` / `port`만 지정합니다:

  * `io`가 지정되면 호스트/포트 정보를 읽는 데 사용됩니다. Julia 워커는 시작 시 바인드 주소와 포트를 출력합니다. 이를 통해 Julia 워커는 워커 포트를 수동으로 구성할 필요 없이 사용 가능한 모든 무료 포트에서 수신 대기할 수 있습니다.
  * `io`가 지정되지 않으면 `host`와 `port`가 연결에 사용됩니다.
  * `count`, `exename` 및 `exeflags`는 작업자에서 추가 작업자를 시작하는 데 관련이 있습니다. 예를 들어, 클러스터 관리자는 노드당 단일 작업자를 시작하고 이를 사용하여 추가 작업자를 시작할 수 있습니다.

      * `count`는 정수 값 `n`을 사용하여 총 `n`명의 작업자를 시작합니다.
      * `count` 값이 `:auto`인 경우 해당 머신의 CPU 스레드(논리 코어) 수만큼의 작업자가 시작됩니다.
      * `exename`은 전체 경로를 포함한 `julia` 실행 파일의 이름입니다.
      * `exeflags`는 새로운 작업자에 대한 필수 명령줄 인수로 설정해야 합니다.
  * `tunnel`, `bind_addr`, `sshflags` 및 `max_parallel`은 마스터 프로세스에서 워커에 연결하기 위해 SSH 터널이 필요할 때 사용됩니다.
  * `userdata`는 사용자 정의 클러스터 관리자가 자신의 작업자별 정보를 저장할 수 있도록 제공됩니다.

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)`는 작업자의 생애 동안 적절한 `op` 값으로 여러 번 호출됩니다:

  * `:register`/`:deregister`를 사용하여 작업자가 Julia 작업자 풀에 추가되거나 제거될 때.
  * `interrupt(workers)`가 호출될 때 `:interrupt`와 함께. `ClusterManager`는 적절한 작업자에게 인터럽트 신호를 보내야 합니다.
  * `:finalize`를 정리 목적으로 사용합니다.

### Cluster Managers with Custom Transports

기본 TCP/IP 모든-대-모든 소켓 연결을 사용자 정의 전송 계층으로 교체하는 것은 조금 더 복잡합니다. 각 Julia 프로세스는 연결된 작업자 수만큼의 통신 작업을 가지고 있습니다. 예를 들어, 모든-대-모든 메쉬 네트워크에서 32개의 프로세스로 구성된 Julia 클러스터를 고려해 보십시오:

  * 각 Julia 프로세스는 따라서 31개의 통신 작업을 가지고 있습니다.
  * 각 작업은 메시지 처리 루프에서 단일 원격 작업자로부터 들어오는 모든 메시지를 처리합니다.
  * 메시지 처리 루프는 `IO` 객체(예: 기본 구현에서 [`TCPSocket`](@ref))에서 대기하고, 전체 메시지를 읽고, 처리한 후 다음 메시지를 기다립니다.
  * 프로세스에 메시지를 보내는 것은 적절한 `IO` 객체를 통해 모든 줄리아 작업에서 직접 수행됩니다. 통신 작업뿐만 아니라 모든 작업에서 가능합니다.

기본 전송을 교체하려면 새로운 구현이 원격 작업자와의 연결을 설정하고 메시지 처리 루프가 대기할 수 있는 적절한 `IO` 객체를 제공해야 합니다. 구현해야 할 관리자별 콜백은 다음과 같습니다:

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

기본 구현(여기서는 TCP/IP 소켓을 사용함)은 `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)`로 구현됩니다.

`connect`는 작업자 `pid`에서 전송된 데이터를 읽기 위한 `IO` 객체와 작업자 `pid`에 전송해야 할 데이터를 쓰기 위한 다른 `IO` 객체의 쌍을 반환해야 합니다. 사용자 정의 클러스터 관리자는 메모리 내 `BufferStream`을 사용하여 사용자 정의, 아마도 비 `IO` 전송과 줄리아의 내장 병렬 인프라 간의 데이터를 프록시하는 데 사용할 수 있습니다.

`BufferStream`은 메모리 내의 [`IOBuffer`](@ref)로, `IO`처럼 동작합니다. 즉, 비동기적으로 처리할 수 있는 스트림입니다.

폴더 `clustermanager/0mq`는 [Examples repository](https://github.com/JuliaAttic/Examples)에 있으며, 여기에는 중간에 0MQ 브로커가 있는 스타 토폴로지에서 Julia 작업자를 연결하기 위해 ZeroMQ를 사용하는 예제가 포함되어 있습니다. 주의: Julia 프로세스는 여전히 모두 *논리적으로* 서로 연결되어 있으며, 어떤 작업자도 0MQ가 전송 계층으로 사용되고 있다는 인식 없이 다른 작업자에게 직접 메시지를 보낼 수 있습니다.

사용자 정의 전송을 사용할 때:

  * Julia 작업자는 `--worker`로 시작해서는 안 됩니다. `--worker`로 시작하면 새로 시작된 작업자가 기본적으로 TCP/IP 소켓 전송 구현을 사용하게 됩니다.
  * 모든 수신 논리 연결에 대해 `Base.process_messages(rd::IO, wr::IO)()`를 호출해야 합니다. 이는 `IO` 객체로 표현된 작업자와의 메시지 읽기 및 쓰기를 처리하는 새로운 작업을 시작합니다.
  * `init_worker(cookie, manager::FooManager)` *는* 작업자 프로세스 초기화의 일환으로 호출되어야 합니다.
  * `WorkerConfig`의 `connect_at::Any` 필드는 [`launch`](@ref)가 호출될 때 클러스터 관리자가 설정할 수 있습니다. 이 필드의 값은 모든 [`connect`](@ref) 콜백에 전달됩니다. 일반적으로 이 필드는 *작업자에 연결하는 방법*에 대한 정보를 담고 있습니다. 예를 들어, TCP/IP 소켓 전송은 이 필드를 사용하여 작업자에 연결할 `(host, port)` 튜플을 지정합니다.

`kill(manager, pid, config)`는 클러스터에서 작업자를 제거하기 위해 호출됩니다. 마스터 프로세스에서는 해당 `IO` 객체가 구현에 의해 닫혀야 적절한 정리가 보장됩니다. 기본 구현은 지정된 원격 작업자에서 단순히 `exit()` 호출을 실행합니다.

Examples 폴더 `clustermanager/simple`는 클러스터 설정을 위해 UNIX 도메인 소켓을 사용하는 간단한 구현을 보여주는 예제입니다.

### Network Requirements for LocalManager and SSHManager

Julia 클러스터는 로컬 노트북, 부서 클러스터 또는 클라우드와 같은 이미 보안이 설정된 환경에서 실행되도록 설계되었습니다. 이 섹션에서는 내장된 `LocalManager` 및 `SSHManager`에 대한 네트워크 보안 요구 사항을 다룹니다:

  * 마스터 프로세스는 어떤 포트에서도 수신하지 않습니다. 오직 워커에게 연결만 합니다.
  * 각 작업자는 로컬 인터페이스 중 하나에만 바인딩하고 OS에 의해 할당된 임시 포트 번호에서 수신 대기합니다.
  * `LocalManager`, `addprocs(N)`에 의해 사용되며, 기본적으로 루프백 인터페이스에만 바인딩됩니다. 이는 나중에 원격 호스트에서 시작된 작업자(또는 악의적인 의도를 가진 누구든지)가 클러스터에 연결할 수 없음을 의미합니다. `addprocs(4)` 다음에 `addprocs(["remote_host"])`를 실행하면 실패합니다. 일부 사용자는 자신의 로컬 시스템과 몇 개의 원격 시스템으로 구성된 클러스터를 생성해야 할 수 있습니다. 이는 `restrict` 키워드 인수를 통해 `LocalManager`에 외부 네트워크 인터페이스에 바인딩하도록 명시적으로 요청함으로써 수행할 수 있습니다: `addprocs(4; restrict=false)`.
  * `SSHManager`는 `addprocs(list_of_remote_hosts)`에 의해 원격 호스트에서 SSH를 통해 작업자를 시작합니다. 기본적으로 SSH는 Julia 작업자를 시작하는 데만 사용됩니다. 이후의 마스터-작업자 및 작업자-작업자 연결은 일반적인 암호화되지 않은 TCP/IP 소켓을 사용합니다. 원격 호스트는 비밀번호 없는 로그인이 활성화되어 있어야 합니다. 추가 SSH 플래그나 자격 증명은 키워드 인수 `sshflags`를 통해 지정할 수 있습니다.
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)`는 마스터-워커 간에 SSH 연결을 사용하고자 할 때 유용합니다. 이러한 전형적인 시나리오는 로컬 노트북에서 Julia REPL(즉, 마스터)을 실행하고 나머지 클러스터는 클라우드, 예를 들어 Amazon EC2에서 실행되는 경우입니다. 이 경우 원격 클러스터에서 포트 22만 열려 있으면 되며, 공개 키 기반 구조(PKI)를 통해 인증된 SSH 클라이언트가 필요합니다. 인증 자격 증명은 `sshflags`를 통해 제공할 수 있으며, 예를 들어 ```sshflags=`-i <keyfile>` ```.

    모든 작업자가 서로 연결되는 올-투-올(topology) 토폴로지(기본값)에서는 모든 작업자가 일반 TCP 소켓을 통해 서로 연결됩니다. 따라서 클러스터 노드의 보안 정책은 작업자 간의 자유로운 연결을 보장해야 하며, 이는 임시 포트 범위(운영 체제에 따라 다름)에 해당합니다.

    모든 작업자 간 트래픽(SSH를 통해)을 보호하고 암호화하거나 개별 메시지를 암호화하는 것은 사용자 정의 `ClusterManager`를 통해 수행할 수 있습니다.
  * `multiplex=true`를 [`addprocs`](@ref) 옵션으로 지정하면, SSH 멀티플렉싱을 사용하여 마스터와 워커 간의 터널이 생성됩니다. SSH 멀티플렉싱을 직접 구성하고 연결이 이미 설정된 경우, `multiplex` 옵션과 관계없이 SSH 멀티플렉싱이 사용됩니다. 멀티플렉싱이 활성화되면, 기존 연결을 사용하여 포워딩이 설정됩니다(`-O forward` 옵션을 ssh에서 사용). 이는 서버가 비밀번호 인증을 요구하는 경우 유용합니다. `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566`에 앞서 서버에 로그인하여 Julia에서 인증을 피할 수 있습니다. 제어 소켓은 세션 동안 `~/.ssh/julia-%r@%h:%p`에 위치하게 되며, 기존 멀티플렉싱 연결이 사용되지 않는 한 그렇습니다. 노드에서 여러 프로세스를 생성하고 멀티플렉싱을 활성화하면 대역폭이 제한될 수 있다는 점에 유의하세요. 이 경우 프로세스는 단일 멀티플렉싱 TCP 연결을 공유하기 때문입니다.

### [Cluster Cookie](@id man-cluster-cookie)

클러스터의 모든 프로세스는 동일한 쿠키를 공유하며, 기본적으로 이는 마스터 프로세스에서 무작위로 생성된 문자열입니다:

  * [`cluster_cookie()`](@ref)는 쿠키를 반환하고, `cluster_cookie(cookie)()`는 쿠키를 설정하고 새로운 쿠키를 반환합니다.
  * 모든 연결은 양쪽에서 인증되어 마스터에 의해 시작된 작업자만 서로 연결할 수 있도록 보장합니다.
  * 쿠키는 시작 시 인수 `--worker=<cookie>`를 통해 작업자에게 전달될 수 있습니다. 인수 `--worker`가 쿠키 없이 지정되면, 작업자는 표준 입력([`stdin`](@ref))에서 쿠키를 읽으려고 시도합니다. 쿠키가 검색된 후 `stdin`은 즉시 닫힙니다.
  * `ClusterManager`는 [`cluster_cookie()`](@ref)를 호출하여 마스터에서 쿠키를 검색할 수 있습니다. 기본 TCP/IP 전송을 사용하지 않는 클러스터 관리자는 (따라서 `--worker`를 지정하지 않음) 마스터와 동일한 쿠키로 `init_worker(cookie, manager)`를 호출해야 합니다.

보안 수준이 높은 환경에서는 사용자 정의 `ClusterManager`를 통해 이를 구현할 수 있습니다. 예를 들어, 쿠키는 미리 공유될 수 있으므로 시작 인수로 지정되지 않을 수 있습니다.

## Specifying Network Topology (Experimental)

`topology` 키워드 인자는 [`addprocs`](@ref)에 전달되어 작업자들이 서로 어떻게 연결되어야 하는지를 지정하는 데 사용됩니다:

  * `:all_to_all`, 기본값: 모든 작업자가 서로 연결되어 있습니다.
  * `:master_worker`: 오직 드라이버 프로세스, 즉 `pid` 1만이 워커와 연결되어 있습니다.
  * `:custom`: 클러스터 관리자의 `launch` 메서드는 `WorkerConfig`의 `ident` 및 `connect_idents` 필드를 통해 연결 토폴로지를 지정합니다. 클러스터 관리자에서 제공하는 아이덴티티 `ident`를 가진 워커는 `connect_idents`에 지정된 모든 워커에 연결됩니다.

키워드 인수 `lazy=true|false`는 `topology` 옵션 `:all_to_all`에만 영향을 미칩니다. `true`인 경우, 클러스터는 마스터가 모든 워커에 연결된 상태로 시작합니다. 특정 워커-워커 연결은 두 워커 간의 첫 번째 원격 호출에서 설정됩니다. 이는 클러스터 내 통신을 위해 할당되는 초기 리소스를 줄이는 데 도움이 됩니다. 연결은 병렬 프로그램의 런타임 요구 사항에 따라 설정됩니다. `lazy`의 기본값은 `true`입니다.

현재 연결되지 않은 작업자 간에 메시지를 보내면 오류가 발생합니다. 이 동작은 기능 및 인터페이스와 마찬가지로 실험적인 성격으로 간주되어야 하며, 향후 릴리스에서 변경될 수 있습니다.

## Noteworthy external packages

Outside of Julia parallelism there are plenty of external packages that should be mentioned. For example, [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) is a Julia wrapper for the `MPI` protocol, [`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) provides functionality similar to Python's [Dask](https://dask.org/), and [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) provides array operations distributed across workers, as [outlined above](@ref man-shared-arrays).

Julia의 GPU 프로그래밍 생태계에 대한 언급이 있어야 하며, 여기에는:

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl)는 다양한 CUDA 라이브러리를 래핑하고 Nvidia GPU용 Julia 커널 컴파일을 지원합니다.
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl)는 oneAPI 통합 프로그래밍 모델을 래핑하며, 지원되는 가속기에서 Julia 커널을 실행하는 것을 지원합니다. 현재는 Linux만 지원됩니다.
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl)는 AMD ROCm 라이브러리를 래핑하고 AMD GPU용 Julia 커널 컴파일을 지원합니다. 현재는 Linux만 지원됩니다.
4. 고급 라이브러리인 [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [Tullio.jl](https://github.com/mcabbott/Tullio.jl) 및 [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl).

다음 예제에서는 `DistributedArrays.jl`와 `CUDA.jl`을 사용하여 배열을 여러 프로세스에 분산시키기 위해 먼저 `distribute()`와 `CuArray()`를 통해 캐스팅합니다.

`DistributedArrays.jl`를 가져올 때 [`@everywhere`](@ref)를 사용하여 모든 프로세스에서 가져오는 것을 기억하세요.

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

다음 예제에서는 `DistributedArrays.jl`와 `CUDA.jl`을 사용하여 배열을 여러 프로세스에 분산시키고 그 위에서 일반 함수를 호출합니다.

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method`는 반복적으로 새로운 벡터를 생성하고 이를 정규화합니다. 함수 선언에서 어떤 타입 서명을 지정하지 않았으므로, 앞서 언급한 데이터 타입으로 작동하는지 확인해 봅시다:

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

이 외부 패키지에 대한 짧은 노출을 마치기 위해, 우리는 `MPI.jl`을 고려할 수 있습니다. 이는 MPI 프로토콜의 줄리아 래퍼입니다. 모든 내부 함수를 고려하는 데 너무 오랜 시간이 걸리므로, 프로토콜을 구현하는 데 사용된 접근 방식을 간단히 감상하는 것이 더 좋습니다.

이 장난감 스크립트는 각 하위 프로세스를 호출하고 그 순위를 인스턴스화하며, 마스터 프로세스에 도달했을 때 순위의 합계를 수행합니다.

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).
