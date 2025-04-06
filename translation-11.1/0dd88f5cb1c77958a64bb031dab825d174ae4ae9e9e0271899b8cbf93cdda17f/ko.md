# Profiling

`Profile` 모듈은 개발자가 코드 성능을 개선하는 데 도움이 되는 도구를 제공합니다. 사용 시 실행 중인 코드에 대한 측정을 수행하고, 개별 줄에서 소요되는 시간을 이해하는 데 도움이 되는 출력을 생성합니다. 가장 일반적인 사용법은 최적화의 목표로 "병목 현상"을 식별하는 것입니다.

`Profile`는 "샘플링" 또는 [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming))로 알려진 것을 구현합니다. 이는 작업 실행 중 주기적으로 백트레이스를 가져오는 방식으로 작동합니다. 각 백트레이스는 현재 실행 중인 함수와 줄 번호, 그리고 이 줄로 이어지는 함수 호출의 전체 체인을 캡처하여 현재 실행 상태의 "스냅샷"을 제공합니다.

특정 코드 줄을 실행하는 데 많은 실행 시간이 소요된다면, 이 줄은 모든 백트레이스 집합에서 자주 나타날 것입니다. 다시 말해, 주어진 줄의 "비용"—혹은 실제로 이 줄까지 포함한 함수 호출의 순서의 비용—은 모든 백트레이스 집합에서 얼마나 자주 나타나는지에 비례합니다.

샘플링 프로파일러는 완전한 라인별 커버리지를 제공하지 않습니다. 이는 백트레이스가 간격을 두고 발생하기 때문입니다(기본적으로 Unix 시스템에서는 1ms, Windows에서는 10ms이며, 실제 스케줄링은 운영 체제의 부하에 따라 달라질 수 있습니다). 또한, 아래에서 더 논의하듯이, 샘플이 모든 실행 지점의 희소한 하위 집합에서 수집되기 때문에 샘플링 프로파일러가 수집하는 데이터는 통계적 노이즈의 영향을 받을 수 있습니다.

이러한 한계에도 불구하고 샘플링 프로파일러는 상당한 강점을 가지고 있습니다:

  * 코드에 타이밍 측정을 위한 수정이 필요하지 않습니다.
  * Julia의 핵심 코드와 심지어 (선택적으로) C 및 Fortran 라이브러리로 프로파일링할 수 있습니다.
  * "드물게" 실행함으로써 성능 오버헤드가 거의 없으며, 프로파일링 중에는 코드가 거의 네이티브 속도로 실행될 수 있습니다.

이러한 이유로, 대안들을 고려하기 전에 내장 샘플링 프로파일러를 사용해보는 것이 권장됩니다.

## Basic usage

간단한 테스트 케이스로 작업해 봅시다:

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

코드를 프로파일링하려는 경우, 최소한 한 번은 실행하는 것이 좋습니다(줄리아의 JIT 컴파일러를 프로파일링하려는 경우를 제외하고):

```julia-repl
julia> myfunc() # run once to force compilation
```

이제 이 함수를 프로파일링할 준비가 되었습니다:

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

프로파일링 결과를 보려면 여러 그래픽 브라우저가 있습니다. 하나의 "가족" 시각화 도구는 [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl)를 기반으로 하며, 각 가족 구성원은 서로 다른 사용자 인터페이스를 제공합니다:

  * [VS Code](https://www.julia-vscode.org/)는 프로필 시각화를 위한 내장 지원이 있는 전체 IDE입니다.
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl)는 GTK를 기반으로 한 독립형 시각화 도구입니다.
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl)는 VegaLight를 사용하며 Jupyter 노트북과 잘 통합됩니다.
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl)는 HTML을 생성하고 추가 요약을 제공하며 Jupyter 노트북과 잘 통합됩니다.
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl)는 SVG를 렌더링합니다.
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)는 그래프, 플레임 그래프 등을 검사하기 위한 로컬 웹사이트를 제공합니다.
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)는 [Julia VS Code extension](https://www.julia-vscode.org/)에 의해 사용되는 HTML 캔버스 기반 프로필 뷰어 UI로, 인터랙티브 HTML 파일도 생성할 수 있습니다.

완전히 독립적인 프로파일 시각화 접근 방식은 [PProf.jl](https://github.com/vchuravy/PProf.jl)로, 외부 `pprof` 도구를 사용합니다.

여기서는 표준 라이브러리와 함께 제공되는 텍스트 기반 디스플레이를 사용할 것입니다:

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

이 디스플레이의 각 줄은 코드의 특정 위치(줄 번호)를 나타냅니다. 들여쓰기는 함수 호출의 중첩 순서를 나타내며, 더 많이 들여쓰기된 줄은 호출 순서에서 더 깊은 위치에 있습니다. 각 줄에서 첫 번째 "필드"는 *이 줄에서 또는 이 줄에 의해 실행된 함수에서* 가져온 백트레이스(샘플)의 수입니다. 두 번째 필드는 파일 이름과 줄 번호이며, 세 번째 필드는 함수 이름입니다. 특정 줄 번호는 Julia의 코드가 변경됨에 따라 변경될 수 있으므로, 따라가고 싶다면 이 예제를 직접 실행하는 것이 가장 좋습니다.

이 예제에서 우리는 호출된 최상위 함수가 `event.jl` 파일에 있음을 알 수 있습니다. 이 함수는 Julia를 실행할 때 REPL을 실행하는 함수입니다. `REPL.jl`의 97번째 줄을 살펴보면 `eval_user_input()` 함수가 호출되는 곳을 볼 수 있습니다. 이 함수는 REPL에서 입력한 내용을 평가하는 함수이며, 우리가 상호작용적으로 작업하고 있기 때문에 `@profile myfunc()`를 입력했을 때 이러한 함수가 호출되었습니다. 다음 줄은 [`@profile`](@ref) 매크로에서 수행된 작업을 반영합니다.

첫 번째 줄은 `event.jl`의 73번째 줄에서 80개의 백트레이스가 수집되었음을 보여주지만, 이 줄이 "비용이 많이 드는" 것은 아닙니다: 세 번째 줄은 이 80개의 백트레이스가 실제로 `eval_user_input` 호출 내부에서 발생했음을 드러냅니다. 어떤 작업이 실제로 시간을 소모하는지 알아내기 위해서는 호출 체인을 더 깊이 살펴봐야 합니다.

이 출력에서 첫 번째 "중요한" 줄은 다음과 같습니다:

```
52 ./REPL[1]:2; myfunc()
```

`REPL`은 우리가 `myfunc`를 파일에 넣는 대신 REPL에서 정의했음을 나타냅니다. 만약 파일을 사용했다면, 파일 이름이 표시되었을 것입니다. `[1]`은 `myfunc` 함수가 이 REPL 세션에서 평가된 첫 번째 표현식임을 보여줍니다. `myfunc()`의 2번째 줄에는 `rand`에 대한 호출이 포함되어 있으며, 이 줄에서 80개 중 52개의 백트레이스가 발생했습니다. 그 아래에는 `dSFMT.jl` 내의 `dsfmt_fill_array_close_open!`에 대한 호출을 볼 수 있습니다.

조금 더 아래로 가면, 다음을 볼 수 있습니다:

```
28 ./REPL[1]:3; myfunc()
```

`myfunc`의 3번째 줄에는 `maximum` 호출이 포함되어 있으며, 여기서 80개 중 28개의 백트레이스가 수집되었습니다. 그 아래에는 이 유형의 입력 데이터에 대한 `maximum` 함수에서 시간 소모적인 작업을 수행하는 `base/reduce.jl`의 특정 위치를 볼 수 있습니다.

전반적으로, 무작위 숫자를 생성하는 것이 최대 요소를 찾는 것보다 대략 두 배 더 비용이 든다고 잠정적으로 결론지을 수 있습니다. 더 많은 샘플을 수집함으로써 이 결과에 대한 신뢰도를 높일 수 있습니다:

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

일반적으로, 선에서 수집된 `N` 샘플이 있다면, 다른 소음 원인(예: 컴퓨터가 다른 작업으로 바쁜 경우)을 제외하고 `sqrt(N)` 정도의 불확실성을 기대할 수 있습니다. 이 규칙의 주요 예외는 가비지 컬렉션으로, 드물게 실행되지만 상당히 비용이 많이 듭니다. (줄리아의 가비지 컬렉터는 C로 작성되었기 때문에, 아래 설명된 `C=true` 출력 모드를 사용하거나 [ProfileView.jl](https://github.com/timholy/ProfileView.jl)를 사용하여 이러한 이벤트를 감지할 수 있습니다.)

이것은 기본 "트리" 덤프를 보여줍니다. 대안으로는 중첩과 무관하게 카운트를 누적하는 "플랫" 덤프가 있습니다:

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

재귀가 있는 코드에서는 "자식" 함수의 한 줄이 전체 백트레이스보다 더 많은 카운트를 누적할 수 있다는 점이 혼란스러울 수 있습니다. 다음 함수 정의를 고려해 보세요:

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

`dumbsum3`를 프로파일링하고 있을 때 `dumbsum(1)`을 실행하는 동안 백트레이스가 다음과 같이 보일 것입니다:

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

결과적으로, 이 자식 함수는 3개의 카운트를 얻지만, 부모는 단지 하나만 얻습니다. "트리" 표현은 이를 훨씬 더 명확하게 만들어 주며, 이러한 이유(다른 이유들 중에서)로 인해 결과를 보는 가장 유용한 방법일 것입니다.

## Accumulation and clearing

[`@profile`](@ref)의 결과는 버퍼에 누적됩니다. `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566` 아래에서 여러 코드 조각을 실행하면, [`Profile.print()`](@ref)가 결합된 결과를 보여줍니다. 이는 매우 유용할 수 있지만, 때때로 새로 시작하고 싶을 수 있습니다. 이 경우 [`Profile.clear()`](@ref)를 사용하면 됩니다.

## Options for controlling the display of profile results

[`Profile.print`](@ref)는 지금까지 설명한 것보다 더 많은 옵션을 가지고 있습니다. 전체 선언을 살펴보겠습니다:

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

먼저 두 개의 위치 인수에 대해 논의한 후, 키워드 인수에 대해 이야기합시다:

  * `io` – 결과를 버퍼에 저장할 수 있게 해줍니다. 예를 들어 파일에 저장할 수 있지만, 기본값은 `stdout`(콘솔)에 출력하는 것입니다.
  * `data` – 분석하려는 데이터를 포함합니다. 기본적으로 이는 [`Profile.fetch()`](@ref)에서 가져오며, 이는 미리 할당된 버퍼에서 백트레이스를 추출합니다. 예를 들어, 프로파일러를 프로파일링하고 싶다면 다음과 같이 말할 수 있습니다:

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

키워드 인수는 다음의 조합일 수 있습니다:

  * `format` – 위에서 소개된 대로, 백트레이스가 트리 구조를 나타내는 들여쓰기와 함께 (기본값, `:tree`) 또는 없이 (`:flat`) 인쇄되는지를 결정합니다.
  * `C` – `true`인 경우 C 및 Fortran 코드에서의 백트레이스가 표시됩니다(정상적으로는 제외됨). `Profile.print(C = true)`를 사용하여 소개 예제를 실행해 보세요. 이는 병목 현상을 일으키는 코드가 Julia인지 C인지 결정하는 데 매우 유용할 수 있습니다. `C = true`로 설정하면 프로파일 덤프가 길어지는 대신 중첩의 해석 가능성이 향상됩니다.
  * `combine` – 일부 코드 줄은 여러 작업을 포함합니다. 예를 들어, `s += A[i]`는 배열 참조(`A[i]`)와 합산 작업을 모두 포함합니다. 이는 생성된 기계 코드에서 서로 다른 줄에 해당하며, 따라서 이 줄에서 백트레이스 중에 두 개 이상의 서로 다른 주소가 캡처될 수 있습니다. `combine = true`는 이들을 함께 묶으며, 이는 일반적으로 원하는 방식일 것입니다. 그러나 `combine = false`로 설정하면 각 고유한 명령 포인터에 대해 별도로 출력을 생성할 수 있습니다.
  * `maxdepth` – `:tree` 형식에서 `maxdepth`보다 깊이가 높은 프레임을 제한합니다.
  * `sortedby` – `:flat` 형식에서 순서를 제어합니다. 기본값인 `:filefuncline`은 소스 라인에 따라 정렬하고, `:count`는 수집된 샘플 수에 따라 정렬합니다.
  * `noisefloor` – 샘플의 휴리스틱 노이즈 플로어 아래에 있는 프레임을 제한합니다(형식 `:tree`에만 적용됨). 이를 위해 시도해 볼 수 있는 제안 값은 2.0입니다(기본값은 0입니다). 이 매개변수는 `n <= noisefloor * √N`인 샘플을 숨깁니다. 여기서 `n`은 이 줄의 샘플 수이고, `N`은 호출자의 샘플 수입니다.
  * `mincount` – `mincount` 발생 횟수가 미만인 프레임을 제한합니다.

File/function names are sometimes truncated (with `...`), and indentation is truncated with a `+n` at the beginning, where `n` is the number of extra spaces that would have been inserted, had there been room. If you want a complete profile of deeply-nested code, often a good idea is to save to a file using a wide `displaysize` in an [`IOContext`](@ref):

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref)는 단순히 백트레이스를 축적하고, 분석은 [`Profile.print()`](@ref)를 호출할 때 발생합니다. 장기 실행되는 계산의 경우, 백트레이스를 저장하기 위한 미리 할당된 버퍼가 가득 차는 것이 전혀 불가능하지 않습니다. 그런 일이 발생하면 백트레이스는 중단되지만 계산은 계속 진행됩니다. 그 결과, 중요한 프로파일링 데이터를 놓칠 수 있습니다(그럴 경우 경고가 표시됩니다).

다음과 같은 방법으로 관련 매개변수를 얻고 구성할 수 있습니다:

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n`은 저장할 수 있는 총 명령 포인터의 수로, 기본값은 `10^6`입니다. 일반적인 백트레이스가 20개의 명령 포인터인 경우, 50000개의 백트레이스를 수집할 수 있으며, 이는 1% 미만의 통계적 불확실성을 나타냅니다. 이는 대부분의 애플리케이션에 충분할 수 있습니다.

결과적으로, 요청된 계산을 수행하기 위해 스냅샷 사이에 Julia가 갖는 시간의 양을 설정하는 `delay`(초 단위)를 수정해야 할 가능성이 더 높습니다. 매우 오랜 시간이 걸리는 작업은 자주 백트레이스를 필요로 하지 않을 수 있습니다. 기본 설정은 `delay = 0.001`입니다. 물론, 지연 시간을 줄일 수도 있고 늘릴 수도 있지만, 지연 시간이 백트레이스를 수행하는 데 필요한 시간(~저자의 노트북에서 약 30마이크로초)과 비슷해지면 프로파일링의 오버헤드가 증가합니다.

## Memory allocation analysis

성능을 향상시키기 위한 가장 일반적인 기술 중 하나는 메모리 할당을 줄이는 것입니다. Julia는 이를 측정하기 위한 여러 도구를 제공합니다:

### `@time`

할당의 총량은 [`@time`](@ref), [`@allocated`](@ref) 및 [`@allocations`](@ref)로 측정할 수 있으며, 특정 할당을 유발하는 라인은 종종 이러한 라인이 발생시키는 가비지 컬렉션 비용을 통해 프로파일링하여 추론할 수 있습니다. 그러나 때때로 각 코드 라인에 의해 할당된 메모리 양을 직접 측정하는 것이 더 효율적일 수 있습니다.

### GC Logging

[`@time`](@ref)는 표현식을 평가하는 동안 메모리 사용량 및 가비지 수집에 대한 고급 통계를 기록하지만, 가비지 수집 이벤트를 각각 기록하는 것도 유용할 수 있습니다. 이를 통해 가비지 수집기가 얼마나 자주 실행되는지, 매번 얼마나 오랫동안 실행되는지, 그리고 매번 얼마나 많은 가비지를 수집하는지 직관적으로 파악할 수 있습니다. 이는 [`GC.enable_logging(true)`](@ref)를 사용하여 활성화할 수 있으며, 이는 Julia가 가비지 수집이 발생할 때마다 stderr에 기록하도록 합니다.

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    이 기능은 최소한 Julia 1.8이 필요합니다.


할당 프로파일러는 실행 중에 각 할당의 스택 추적, 유형 및 크기를 기록합니다. [`Profile.Allocs.@profile`](@ref)로 호출할 수 있습니다.

이 할당에 대한 정보는 `Alloc` 객체의 배열로 반환되며, `AllocResults` 객체에 래핑됩니다. 현재 이를 시각화하는 가장 좋은 방법은 [PProf.jl](https://github.com/JuliaPerf/PProf.jl) 및 [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) 패키지를 사용하는 것입니다. 이 패키지는 가장 많은 할당을 발생시키는 호출 스택을 시각화할 수 있습니다.

할당 프로파일러는 상당한 오버헤드가 있으므로, 일부 할당을 건너뛰어 속도를 높이기 위해 `sample_rate` 인수를 전달할 수 있습니다. `sample_rate=1.0`을 전달하면 모든 것을 기록하게 되며(느림), `sample_rate=0.1`은 할당의 10%만 기록하게 됩니다(더 빠름) 등.

!!! compat "Julia 1.11"
    이전 버전의 Julia는 모든 경우에 타입을 캡처할 수 없었습니다. 이전 버전의 Julia에서 `Profile.Allocs.UnknownType` 타입의 할당을 보게 되면, 이는 프로파일러가 어떤 타입의 객체가 할당되었는지 알지 못한다는 것을 의미합니다. 이는 주로 컴파일러에 의해 생성된 코드에서 할당이 발생할 때 발생했습니다. 자세한 내용은 [issue #43688](https://github.com/JuliaLang/julia/issues/43688)를 참조하세요.

    Julia 1.11부터 모든 할당은 보고된 유형이 있어야 합니다.


이 도구를 사용하는 방법에 대한 자세한 내용은 다음의 JuliaCon 2022 강의를 참조하십시오: https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

이 간단한 예제에서는 PProf를 사용하여 할당 프로파일을 시각화합니다. 대신 다른 시각화 도구를 사용할 수도 있습니다. 우리는 프로파일을 수집하고(샘플링 비율을 지정하여) 이를 시각화합니다.

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

여기 샘플 비율을 조정하는 방법을 보여주는 더 심층적인 예가 있습니다. 목표로 삼을 좋은 샘플 수는 약 1,000 - 10,000개입니다. 너무 많으면 프로파일 시각화 도구가 과부하에 걸릴 수 있고, 프로파일링이 느려질 수 있습니다. 너무 적으면 대표 샘플이 없게 됩니다.

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

그런 다음 http://localhost:62261로 이동하여 프로필을 볼 수 있으며, 프로필은 디스크에 저장됩니다. 더 많은 옵션은 PProf 패키지를 참조하세요.

##### Allocation Profiling Tips

위에서 언급한 바와 같이, 프로필에 약 1-10천 개의 샘플을 목표로 하세요.

모든 할당의 공간에서 균일하게 샘플링하고 있으며, 할당의 크기로 샘플을 가중치 부여하지 않고 있습니다. 따라서 특정 할당 프로필은 `sample_rate=1`로 설정하지 않는 한 프로그램에서 대부분의 바이트가 할당되는 위치에 대한 대표적인 프로필을 제공하지 않을 수 있습니다.

할당은 사용자가 직접 객체를 구성하여 발생할 수 있지만, 런타임 내부에서 발생하거나 타입 불안정을 처리하기 위해 컴파일된 코드에 삽입될 수도 있습니다. "소스 코드" 뷰를 살펴보는 것은 이를 분리하는 데 도움이 될 수 있으며, 그 후 [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl)와 같은 다른 외부 도구가 할당의 원인을 식별하는 데 유용할 수 있습니다.

##### Allocation Profile Visualization Tools

현재 할당 프로필을 표시할 수 있는 여러 프로파일링 시각화 도구가 있습니다. 우리가 알고 있는 주요 도구 중 일부의 작은 목록은 다음과 같습니다:

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * VSCode의 내장 프로파일 시각화 도구(`@profview_allocs`) [문서 필요]
  * REPL에서 결과를 직접 보기

      * 결과는 [`Profile.Allocs.fetch()`](@ref)를 통해 REPL에서 확인할 수 있으며, 각 할당의 스택 추적 및 유형을 볼 수 있습니다.

#### Line-by-Line Allocation Tracking

할당을 측정하는 대안적인 방법은 `--track-allocation=<setting>` 명령줄 옵션으로 Julia를 시작하는 것입니다. 여기서 `none`(기본값, 할당 측정하지 않음), `user`(Julia의 핵심 코드를 제외한 모든 곳에서 메모리 할당 측정), 또는 `all`(각 줄의 Julia 코드에서 메모리 할당 측정) 중에서 선택할 수 있습니다. 할당은 컴파일된 코드의 각 줄에 대해 측정됩니다. Julia를 종료하면 누적 결과가 파일 이름 뒤에 `.mem`이 추가된 텍스트 파일에 기록되며, 소스 파일과 동일한 디렉토리에 위치합니다. 각 줄은 할당된 총 바이트 수를 나열합니다. [`Coverage` package](https://github.com/JuliaCI/Coverage.jl)는 할당된 바이트 수에 따라 줄을 정렬하는 등의 기본 분석 도구를 포함하고 있습니다.

결과를 해석할 때 몇 가지 중요한 세부 사항이 있습니다. `user` 설정에서 REPL에서 직접 호출된 모든 함수의 첫 번째 줄은 REPL 코드 자체에서 발생하는 이벤트로 인해 할당이 발생합니다. 더 중요한 것은 JIT 컴파일이 할당 수에 추가된다는 점입니다. 왜냐하면 Julia의 컴파일러 대부분이 Julia로 작성되어 있으며(컴파일에는 일반적으로 메모리 할당이 필요함) 그렇기 때문입니다. 권장 절차는 분석하려는 모든 명령을 실행하여 컴파일을 강제한 다음 [`Profile.clear_malloc_data()`](@ref)를 호출하여 모든 할당 카운터를 재설정하는 것입니다. 마지막으로 원하는 명령을 실행하고 Julia를 종료하여 `.mem` 파일 생성을 트리거합니다.

!!! note
    `--track-allocation`는 코드 생성을 변경하여 할당을 기록하므로, 이 옵션 없이 발생하는 것과는 할당이 다를 수 있습니다. 대신 [allocation profiler](@ref allocation-profiler)를 사용하는 것을 권장합니다.


## External Profiling

현재 Julia는 외부 프로파일링 도구로 `Intel VTune`, `OProfile` 및 `perf`를 지원합니다.

선택한 도구에 따라 `Make.user`에서 `USE_INTEL_JITEVENTS`, `USE_OPROFILE_JITEVENTS` 및 `USE_PERF_JITEVENTS`를 1로 설정하여 컴파일합니다. 여러 플래그를 지원합니다.

줄리아를 실행하기 전에 환경 변수 [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING)를 1로 설정하세요.

이제 이러한 도구를 활용할 수 있는 다양한 방법이 있습니다! 예를 들어 `OProfile`을 사용하여 간단한 기록을 시도할 수 있습니다:

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

또는 `perf`와 유사하게:

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

프로그램에 대해 측정할 수 있는 더 많은 흥미로운 것들이 있습니다. 포괄적인 목록을 보려면 [Linux perf examples page](https://www.brendangregg.com/perf.html)를 읽어보세요.

각 실행에 대해 `perf.data` 파일이 저장되며, 작은 프로그램의 경우에도 꽤 커질 수 있습니다. 또한 perf LLVM 모듈은 임시로 디버그 객체를 `~/.debug/jit`에 저장하므로, 해당 폴더를 자주 정리하는 것을 잊지 마세요.
