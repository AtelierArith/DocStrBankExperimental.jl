```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

[`Logging`](@ref Logging.Logging) 모듈은 이벤트 로그로서 계산의 역사와 진행 상황을 기록하는 방법을 제공합니다. 이벤트는 소스 코드에 로깅 문을 삽입하여 생성됩니다. 예를 들어:

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

시스템은 `println()` 호출로 소스 코드를 여기저기 채우는 것에 비해 여러 가지 장점을 제공합니다. 첫째, 소스 코드를 편집하지 않고도 메시지의 가시성과 표현을 제어할 수 있습니다. 예를 들어, 위의 `@warn`과 대조적으로

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

기본적으로 출력이 생성되지 않습니다. 또한, 시스템이 나중에 무시될 경우 메시지를 평가하지 않기 때문에 소스 코드에 이러한 디버그 문을 남기는 것은 매우 저렴합니다. 이 경우 `sum(rand(100))`와 관련된 문자열 처리는 디버그 로깅이 활성화되지 않는 한 절대 실행되지 않습니다.

둘째, 로깅 도구를 사용하면 각 이벤트에 임의의 데이터를 키-값 쌍의 집합으로 첨부할 수 있습니다. 이를 통해 나중에 분석을 위해 로컬 변수 및 기타 프로그램 상태를 캡처할 수 있습니다. 예를 들어, 로컬 배열 변수 `A`와 벡터 `v`의 합계를 키 `s`로 첨부하려면 다음을 사용할 수 있습니다.

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

모든 로깅 매크로 `@debug`, `@info`, `@warn` 및 `@error`는 더 일반적인 매크로 [`@logmsg`](@ref)의 문서에 자세히 설명된 공통 기능을 공유합니다.

## Log event structure

각 이벤트는 여러 개의 데이터를 생성하며, 일부는 사용자가 제공하고 일부는 자동으로 추출됩니다. 먼저 사용자 정의 데이터를 살펴보겠습니다:

  * *로그 레벨*은 초기 필터링에 사용되는 메시지의 광범위한 범주입니다. 여러 표준 수준이 있으며, [`LogLevel`](@ref) 유형이 있습니다. 사용자 정의 레벨도 가능합니다. 각 레벨은 목적이 다릅니다:

      * [`Logging.Debug`](@ref) (로그 레벨 -1000)은 프로그램 개발자를 위한 정보입니다. 이러한 이벤트는 기본적으로 비활성화되어 있습니다.
      * [`Logging.Info`](@ref) (로그 레벨 0)은 사용자에게 일반 정보를 제공하는 것입니다. 이를 `println`을 직접 사용하는 대안으로 생각하세요.
      * [`Logging.Warn`](@ref) (로그 레벨 1000)은 문제가 발생했음을 의미하며 조치가 필요할 가능성이 있지만 현재 프로그램은 여전히 작동 중임을 나타냅니다.
      * [`Logging.Error`](@ref) (로그 레벨 2000)은 문제가 발생했음을 의미하며, 적어도 이 코드 부분에서는 복구될 가능성이 낮습니다. 종종 이 로그 레벨은 불필요하며, 예외를 던지는 것이 필요한 모든 정보를 전달할 수 있습니다.
  * *메시지*는 이벤트를 설명하는 객체입니다. 관례적으로 메시지로 전달된 `AbstractString`은 마크다운 형식으로 간주됩니다. 다른 유형은 텍스트 기반 출력을 위해 `print(io, obj)` 또는 `string(obj)`를 사용하여 표시되며, 설치된 로거에서 사용되는 다른 멀티미디어 디스플레이를 위해 `show(io,mime,obj)`를 사용할 수 있습니다.
  * 선택적 *키–값 쌍*은 각 이벤트에 임의의 데이터를 첨부할 수 있게 해줍니다. 일부 키는 이벤트 해석 방식에 영향을 줄 수 있는 관례적인 의미를 가지고 있습니다 (참조: [`@logmsg`](@ref)).

시스템은 각 이벤트에 대한 일부 표준 정보를 생성합니다:

  * 로깅 매크로가 확장된 `모듈`.
  * 로깅 매크로가 소스 코드에서 발생하는 `file`과 `line`.
  * 고유하고 고정된 식별자인 메시지 `id`는 로깅 매크로가 나타나는 *소스 코드 문장*을 나타냅니다. 이 식별자는 파일의 소스 코드가 변경되더라도 로깅 문장이 동일하게 유지되는 한 상당히 안정적으로 설계되었습니다.
  * 이벤트에 대한 `group`은 기본적으로 파일의 기본 이름(확장자 제외)으로 설정됩니다. 이는 로그 수준보다 더 세분화된 범주로 메시지를 그룹화하는 데 사용될 수 있습니다(예: 모든 사용 중단 경고는 그룹 `:depwarn`을 가집니다) 또는 모듈 간 또는 모듈 내에서 논리적 그룹으로 묶는 데 사용될 수 있습니다.

기본적으로 이벤트 시간과 같은 유용한 정보가 포함되어 있지 않다는 점에 유의하세요. 이는 이러한 정보를 추출하는 데 비용이 많이 들 수 있으며 현재 로거에 *동적으로* 제공되기 때문입니다. 필요한 경우 시간, 백트레이스, 전역 변수의 값 및 기타 유용한 정보로 이벤트 데이터를 보강하기 위해 [custom logger](@ref AbstractLogger-interface)를 정의하는 것은 간단합니다.

## Processing log events

예제에서 볼 수 있듯이, 로깅 문장은 로그 이벤트가 어디로 가는지 또는 어떻게 처리되는지에 대한 언급이 없습니다. 이는 시스템을 구성 가능하고 동시 사용에 자연스럽게 만드는 핵심 설계 기능입니다. 이는 두 가지 다른 관심사를 분리함으로써 이루어집니다:

  * *로그* 이벤트를 생성하는 것은 이벤트가 발생하는 위치와 포함할 정보를 결정해야 하는 모듈 작성자의 문제입니다.
  * *로그 이벤트의 처리* — 즉, 표시, 필터링, 집계 및 기록 — 는 여러 모듈을 협력하는 애플리케이션으로 통합해야 하는 애플리케이션 저자의 관심사입니다.

### Loggers

이벤트 처리는 *로거*에 의해 수행되며, 이는 이벤트를 처음으로 볼 수 있는 사용자 구성 가능 코드의 첫 번째 조각입니다. 모든 로거는 [`AbstractLogger`](@ref)의 하위 유형이어야 합니다.

이벤트가 트리거되면, 적절한 로거는 글로벌 로거를 대체로 사용하여 작업-로컬 로거를 찾아서 결정됩니다. 여기서의 아이디어는 애플리케이션 코드가 로그 이벤트가 어떻게 처리되어야 하는지를 알고 있으며, 호출 스택의 맨 위 어딘가에 존재한다는 것입니다. 따라서 우리는 호출 스택을 통해 로거를 찾아야 합니다. 즉, 로거는 *동적으로 범위가 지정되어야* 합니다. (이는 로거가 *어휘적으로 범위가 지정된* 로깅 프레임워크와 대조되는 점입니다. 이러한 시스템에서는 모듈 작성자에 의해 명시적으로 제공되거나 단순한 글로벌 변수로 제공됩니다. 이러한 시스템에서는 여러 모듈에서 기능을 조합할 때 로깅을 제어하는 것이 불편합니다.)

전역 로거는 [`global_logger`](@ref)로 설정할 수 있으며, 작업 로컬 로거는 [`with_logger`](@ref)를 사용하여 제어됩니다. 새로 생성된 작업은 부모 작업의 로거를 상속받습니다.

라이브러리에서 제공하는 세 가지 로거 유형이 있습니다. [`ConsoleLogger`](@ref)는 REPL을 시작할 때 볼 수 있는 기본 로거입니다. 이 로거는 이벤트를 읽기 쉬운 텍스트 형식으로 표시하며, 형식 지정 및 필터링에 대한 간단하지만 사용자 친화적인 제어를 제공합니다. [`NullLogger`](@ref)는 필요할 때 모든 메시지를 삭제하는 편리한 방법입니다; 이는 [`devnull`](@ref) 스트림의 로깅에 해당합니다. [`SimpleLogger`](@ref)는 매우 단순한 텍스트 형식 로거로, 주로 로깅 시스템 자체를 디버깅하는 데 유용합니다.

사용자 정의 로거는 [reference section](@ref AbstractLogger-interface)에 설명된 함수에 대한 오버로드를 제공해야 합니다.

### Early filtering and message handling

이벤트가 발생하면, 메시지가 폐기되는 것을 피하기 위해 몇 가지 초기 필터링 단계가 발생합니다:

1. 메시지 로그 수준은 전역 최소 수준( [`disable_logging`](@ref)를 통해 설정됨)과 비교됩니다. 이는 조잡하지만 매우 저렴한 전역 설정입니다.
2. 현재 로거 상태가 조회되고 메시지 레벨이 로거의 캐시된 최소 레벨과 비교됩니다. 이는 [`Logging.min_enabled_level`](@ref)를 호출하여 확인할 수 있습니다. 이 동작은 환경 변수를 통해 재정의할 수 있습니다(자세한 내용은 나중에 설명합니다).
3. [`Logging.shouldlog`](@ref) 함수는 현재 로거와 함께 호출되며, 일부 최소한의 정보(레벨, 모듈, 그룹, ID)를 정적으로 계산할 수 있습니다. 가장 유용하게도, `shouldlog`는 캐시된 술어를 기반으로 이벤트를 조기에 폐기하는 데 사용할 수 있는 이벤트 `id`를 전달받습니다.

모든 검사가 통과하면 메시지와 키-값 쌍이 완전히 평가되어 현재 로거에 [`Logging.handle_message`](@ref) 함수를 통해 전달됩니다. `handle_message()`는 필요에 따라 추가 필터링을 수행하고 이벤트를 화면에 표시하거나 파일에 저장하는 등의 작업을 할 수 있습니다.

로그 이벤트를 생성하는 동안 발생하는 예외는 기본적으로 캡처되어 기록됩니다. 이는 개별적으로 손상된 이벤트가 애플리케이션을 중단시키는 것을 방지하며, 이는 프로덕션 시스템에서 잘 사용되지 않는 디버그 이벤트를 활성화할 때 유용합니다. 이 동작은 [`Logging.catch_exceptions`](@ref)를 확장하여 로거 유형별로 사용자 정의할 수 있습니다.

## Testing log events

로그 이벤트는 일반 코드를 실행하는 부작용이지만, 특정 정보 메시지와 경고를 테스트하고 싶을 수 있습니다. `Test` 모듈은 로그 이벤트 스트림에 대해 패턴 매칭을 수행하는 데 사용할 수 있는 [`@test_logs`](@ref) 매크로를 제공합니다.

## Environment variables

메시지 필터링은 [`JULIA_DEBUG`](@ref JULIA_DEBUG) 환경 변수를 통해 영향을 받을 수 있으며, 파일이나 모듈에 대한 디버그 로깅을 활성화하는 쉬운 방법으로 사용됩니다. `JULIA_DEBUG=loading`으로 줄리아를 로드하면 `loading.jl`에서 `@debug` 로그 메시지가 활성화됩니다. 예를 들어, 리눅스 셸에서:

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

Windows에서는 `CMD`에서 `set JULIA_DEBUG="loading"`을 실행하고, `Powershell`에서는 `$env:JULIA_DEBUG="loading"`을 통해 동일한 작업을 수행할 수 있습니다.

유사하게, 환경 변수를 사용하여 `Pkg`와 같은 모듈 또는 모듈 루트의 디버그 로깅을 활성화할 수 있습니다 (참조: [`Base.moduleroot`](@ref)). 모든 디버그 로깅을 활성화하려면 특별한 값 `all`을 사용하십시오.

REPL에서 디버그 로깅을 켜려면 `ENV["JULIA_DEBUG"]`를 관심 있는 모듈의 이름으로 설정하세요. REPL에서 정의된 함수는 `Main` 모듈에 속하며, 이들에 대한 로깅은 다음과 같이 활성화할 수 있습니다:

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

여러 모듈에 대한 디버그를 활성화하려면 쉼표 구분자를 사용하세요: `JULIA_DEBUG=loading,Main`.

## Examples

### Example: Writing log events to a file

때때로 로그 이벤트를 파일에 기록하는 것이 유용할 수 있습니다. 다음은 작업 로컬 및 전역 로거를 사용하여 정보를 텍스트 파일에 기록하는 방법의 예입니다:

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

여기 [`ConsoleLogger`](@ref)를 생성하는 예가 있습니다. 이 예는 로그 레벨이 [`Logging.Debug`](@ref) 이상인 메시지를 통과시킵니다.

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

이벤트 처리는 `AbstractLogger`와 관련된 함수를 재정의하여 제어됩니다:

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

로거 설치 및 점검:

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

시스템에 공급되는 로거:

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```
