# [Scoped Values](@id scoped-values)

스코프된 값은 Julia에서 동적 스코핑의 구현을 제공합니다.

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables)는 Julia의 기본 동작입니다. 렉시컬 스코프에서 변수의 범위는 프로그램의 렉시컬(텍스트) 구조에 의해 결정됩니다. 다이나믹 스코프에서는 변수가 프로그램 실행 중 가장 최근에 할당된 값에 바인딩됩니다.


스코프된 값의 상태는 프로그램의 실행 경로에 따라 달라집니다. 이는 스코프된 값에 대해 여러 개의 서로 다른 값을 동시에 관찰할 수 있음을 의미합니다.

!!! compat "Julia 1.11"
    Scoped values는 Julia 1.11에서 도입되었습니다. Julia 1.8+에서는 패키지 ScopedValues.jl에서 호환 가능한 구현을 사용할 수 있습니다.


가장 간단한 형태로 [`ScopedValue`](@ref Base.ScopedValues.ScopedValue)를 기본값으로 생성한 다음, [`with`](@ref Base.ScopedValues.with) 또는 [`@with`](@ref Base.ScopedValues.@with)를 사용하여 새로운 동적 범위에 들어갈 수 있습니다. 새로운 범위는 제공된 범위 값이 이전 정의보다 우선하는 방식으로 부모 범위(및 모든 외부 범위에서 재귀적으로)로부터 모든 값을 상속받습니다.

먼저 **어휘** 범위의 예를 살펴보겠습니다. `let` 문은 새로운 어휘 범위를 시작하며, 이 범위 내에서 `x`의 외부 정의는 내부 정의에 의해 가려집니다.

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

다음 예제에서, 줄리아는 렉시컬 스코프를 사용하므로, `f`의 본문에 있는 변수 `x`는 전역 스코프에서 정의된 `x`를 참조하며, `let` 스코프에 들어가도 `f`가 관찰하는 값은 변경되지 않습니다.

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

이제 `ScopedValue`를 사용하여 **동적** 스코프를 사용할 수 있습니다.

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

`ScopedValue`의 관찰된 값은 프로그램의 실행 경로에 따라 달라진다는 점에 유의하세요.

종종 `const` 변수를 사용하여 범위가 있는 값에 포인터를 설정하는 것이 의미가 있으며, 하나의 `with` 호출로 여러 `ScopedValue`의 값을 설정할 수 있습니다.

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues`는 `with`의 매크로 버전을 제공합니다. 표현식 `@with var=>val expr`은 `var`가 `val`로 설정된 새로운 동적 범위에서 `expr`을 평가합니다. `@with var=>val expr`은 `with(var=>val) do expr end`와 동일합니다. 그러나 `with`는 인수가 없는 클로저나 함수를 요구하므로 추가 호출 프레임이 발생합니다. 예를 들어, 다음 함수 `f`를 고려해 보십시오:

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

`f`를 동적 범위에서 `a`를 `2`로 설정하여 실행하려면 `with`를 사용할 수 있습니다:

```julia
with(() -> f(10), a=>2)
```

그러나 이는 `f`를 인수가 없는 함수로 감싸야 합니다. 추가 호출 프레임을 피하고 싶다면 `@with` 매크로를 사용할 수 있습니다:

```julia
@with a=>2 f(10)
```

!!! note
    동적 범위는 작업 생성 시 [`Task`](@ref)에 의해 상속됩니다. 동적 범위는 **전파되지** 않습니다 `Distributed.jl` 작업을 통해.


아래 예제에서는 작업을 시작하기 전에 새로운 동적 범위를 엽니다. 부모 작업과 두 개의 자식 작업은 동시에 동일한 범위 값의 독립적인 값을 관찰합니다.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

스코프 값은 스코프 전반에 걸쳐 일정하지만, 스코프 값에 변경 가능한 상태를 저장할 수 있습니다. 단, 동시 프로그래밍의 맥락에서 전역 변수에 대한 일반적인 주의 사항이 적용된다는 점을 명심하세요.

변경 가능한 상태에 대한 참조를 범위가 있는 값에 저장할 때도 주의가 필요합니다. 새로운 동적 범위에 들어갈 때 명시적으로 [unshare mutable state](@ref unshare_mutable_state)를 원할 수 있습니다.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

아래 예제에서는 웹 애플리케이션에서 권한 검사를 구현하기 위해 스코프된 값을 사용합니다. 요청의 권한을 결정한 후, 새로운 동적 스코프에 들어가고 스코프된 값 `LEVEL`이 설정됩니다. 애플리케이션의 다른 부분은 스코프된 값을 쿼리할 수 있으며 적절한 값을 받게 됩니다. 작업 로컬 저장소나 전역 변수와 같은 다른 대안은 이러한 종류의 전파에 적합하지 않습니다; 우리의 유일한 대안은 전체 호출 체인을 통해 값을 전달하는 것이었을 것입니다.

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

스코프된 값의 값을 접근하기 위해서는 스코프된 값 자체가 (어휘) 스코프 내에 있어야 합니다. 이는 대부분의 경우 스코프된 값을 상수 전역 변수로 사용하고 싶다는 것을 의미합니다.

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

실제로 범위가 있는 값은 숨겨진 함수 인수로 생각할 수 있습니다.

이것은 그들의 비전역 변수로서의 사용을 배제하지 않는다.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

하지만 이러한 경우에는 함수 인수를 직접 전달하는 것이 더 간단했을 것입니다.

### Very many ScopedValues

하나의 모듈에 대해 많은 `ScopedValue`를 생성해야 한다면, 이를 보관할 전용 구조체를 사용하는 것이 더 나을 수 있습니다.

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

`Scope`는 지속적인 사전을 사용합니다. 조회 및 삽입은 `O(log(32, n))`이며, 동적 범위에 진입할 때 소량의 데이터가 복사되고 변경되지 않은 데이터는 다른 범위와 공유됩니다.

`Scope` 객체 자체는 사용자에게 노출되지 않으며, 향후 Julia 버전에서 변경될 수 있습니다.

## Design inspiration

이 디자인은 [JEPS-429](https://openjdk.org/jeps/429)에서 많은 영감을 받았으며, 이는 다시 많은 Lisp 방언에서 동적으로 범위가 지정된 자유 변수에서 영감을 받았습니다. 특히 Interlisp-D와 그 깊은 바인딩 전략이 그렇습니다.

이전에 논의된 디자인은 [PEPS-567](https://peps.python.org/pep-0567/)와 같은 컨텍스트 변수를 포함하며, Julia에서 [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl)로 구현되었습니다.
