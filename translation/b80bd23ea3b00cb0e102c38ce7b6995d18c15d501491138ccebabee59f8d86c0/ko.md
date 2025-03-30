# `EscapeAnalysis`

`Core.Compiler.EscapeAnalysis`는 [Julia's SSA-form IR](@ref Julia-SSA-form-IR) 즉, `IRCode`의 탈출 정보를 분석하는 것을 목표로 하는 컴파일러 유틸리티 모듈입니다.

이 탈출 분석의 목적은:

  * 줄리아의 고수준 의미론을 활용하여, 특히 절차 간 호출을 통해 탈출 및 별칭에 대해 논의합니다.
  * 다양한 최적화에 사용될 수 있을 만큼 다재다능해야 합니다. 여기에는 [alias-aware SROA](https://github.com/JuliaLang/julia/pull/43888), [early `finalize` insertion](https://github.com/JuliaLang/julia/pull/44056), [copy-free `ImmutableArray` construction](https://github.com/JuliaLang/julia/pull/42465), 변경 가능한 객체의 스택 할당 등이 포함됩니다.
  * 간단한 구현을 달성하기 위해 완전한 역방향 데이터 흐름 분석 구현과 직교 격자 속성을 결합한 새로운 격자 설계를 기반으로 합니다.

## Try it out!

`EAUtils.jl` 유틸리티 스크립트를 로드하여 테스트 및 디버깅 목적으로 편리한 항목인 `code_escapes`와 `@code_escapes`를 정의하여 탈출 분석을 시도해 볼 수 있습니다:

```@repl EAUtils
let JULIA_DIR = normpath(Sys.BINDIR, "..", "share", "julia")
    # load `EscapeAnalysis` module to define the core analysis code
    include(normpath(JULIA_DIR, "base", "compiler", "ssair", "EscapeAnalysis", "EscapeAnalysis.jl"))
    using .EscapeAnalysis
    # load `EAUtils` module to define the utilities
    include(normpath(JULIA_DIR, "test", "compiler", "EscapeAnalysis", "EAUtils.jl"))
    using .EAUtils
end

mutable struct SafeRef{T}
    x::T
end
Base.getindex(x::SafeRef) = x.x;
Base.setindex!(x::SafeRef, v) = x.x = v;
Base.isassigned(x::SafeRef) = true;
get′(x) = isassigned(x) ? x[] : throw(x);

result = code_escapes((String,String,String,String)) do s1, s2, s3, s4
    r1 = Ref(s1)
    r2 = Ref(s2)
    r3 = SafeRef(s3)
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    s3 = get′(r3)       # still `r3` doesn't escape fully
    s4 = sizeof(s4)     # the argument `s4` doesn't escape here
    return s2, s3, s4
end
```

각 호출 인수 및 SSA 문 옆의 기호는 다음과 같은 의미를 나타냅니다:

  * `◌` (plain): 이 값은 분석되지 않습니다. 왜냐하면 이 값의 이스케이프 정보는 어차피 사용되지 않기 때문입니다 (예를 들어 객체가 `isbitstype`인 경우).
  * `✓` (녹색 또는 청록색): 이 값은 결코 탈출하지 않습니다 (`has_no_escape(result.state[x])`가 참임), 인수 탈출이 있는 경우 파란색으로 표시됩니다 (`has_arg_escape(result.state[x])`가 참임)
  * `↑` (파랑 또는 노랑): 이 값은 반환을 통해 호출자에게 탈출할 수 있습니다 (`has_return_escape(result.state[x])`가 참일 경우), 처리되지 않은 던져진 탈출이 있을 경우 노란색으로 표시됩니다 (`has_thrown_escape(result.state[x])`가 참일 경우)
  * `X` (빨간색): 이 값은 전역 메모리로의 탈출과 같이 탈출 분석이 추론할 수 없는 곳으로 탈출할 수 있습니다 (`has_all_escape(result.state[x])`가 참입니다)
  * `*` (굵게): 이 값의 이스케이프 상태는 [`EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo)의 부분 순서에서 `ReturnEscape`와 `AllEscape` 사이에 있으며, 처리되지 않은 던져진 이스케이프가 있는 경우 노란색으로 표시됩니다 (`has_thrown_escape(result.state[x])`가 참일 때).
  * `′`: 이 값은 `AliasInfo` 속성에 추가 객체 필드 / 배열 요소 정보가 있습니다.

각 호출 인수 및 SSA 값의 탈출 정보를 프로그래밍 방식으로 검사할 수 있습니다:

```@repl EAUtils
result.state[Core.Argument(3)] # get EscapeInfo of `s2`

result.state[Core.SSAValue(3)] # get EscapeInfo of `r3`
```

## Analysis Design

### Lattice Design

`EscapeAnalysis`는 [data-flow analysis](https://en.wikipedia.org/wiki/Data-flow_analysis)로 구현되며, [`x::EscapeInfo`](@ref Core.Compiler.EscapeAnalysis.EscapeInfo)의 격자에서 작동합니다. 이는 다음 속성으로 구성됩니다:

  * `x.Analyzed::Bool`: 격자의 공식적인 일부는 아니지만, `x`가 분석되지 않았거나 분석되지 않았음을 나타냅니다.
  * `x.ReturnEscape::BitSet`: 호출자에게 반환을 통해 `x`가 탈출할 수 있는 SSA 문을 기록합니다.
  * `x.ThrownEscape::BitSet`: `x`가 예외로 던져질 수 있는 SSA 문을 기록합니다 (아래 설명된 [exception handling](@ref EA-Exception-Handling)에 사용됨)
  * `x.AliasInfo`: `x`의 필드 또는 배열 요소에 별칭을 붙일 수 있는 모든 가능한 값을 유지합니다 (아래에 설명된 [alias analysis](@ref EA-Alias-Analysis)에 사용됨)
  * `x.ArgEscape::Int` (아직 구현되지 않음): 인수에 대해 `setfield!`를 통해 호출자에게 탈출할 것임을 나타냅니다.

이러한 속성들은 입력 프로그램이 유한한 수의 문장을 가지는 불변성을 고려할 때, 유한한 높이를 가진 부분 격자를 생성하기 위해 결합될 수 있습니다. 이 격자 설계의 영리한 부분은 각 격자 속성을 별도로 처리할 수 있도록 하여 격자 연산의 더 간단한 구현을 가능하게 한다는 점입니다[^LatticeDesign].

### Backward Escape Propagation

이 탈출 분석 구현은 논문[^MM02]에 설명된 데이터 흐름 알고리즘을 기반으로 합니다. 이 분석은 `EscapeInfo`의 격자에서 작동하며, 모든 격자 요소가 고정점으로 수렴될 때까지 격자 요소를 아래에서 위로 전이합니다. 이 과정에서 분석할 남은 SSA 문에 해당하는 프로그램 카운터를 포함하는 (개념적) 작업 집합을 유지합니다. 이 분석은 각 인수와 SSA 문에 대한 `EscapeInfo`를 추적하는 단일 전역 상태를 관리하지만, 일부 흐름 민감도는 `EscapeInfo`의 `ReturnEscape` 속성에 기록된 프로그램 카운터로 인코딩되어 있다는 점도 주목해야 합니다. 이는 필요할 경우 흐름 민감도에 대해 추론하기 위해 나중에 지배 분석과 결합될 수 있습니다.

이 탈출 분석의 독특한 설계 중 하나는 완전히 *역방향*이라는 점입니다. 즉, 탈출 정보는 *사용에서 정의로 흐릅니다*. 예를 들어, 아래 코드 조각에서 EA는 먼저 `return %1` 문을 분석하고 `%1`(즉, `obj`에 해당)에 `ReturnEscape`를 부여한 다음, `%1 = %new(Base.RefValue{String, _2}))`를 분석하고 `%1`에 부여된 `ReturnEscape`를 호출 인자 `_2`(즉, `s`에 해당)로 전파합니다.

```@repl EAUtils
code_escapes((String,)) do s
    obj = Ref(s)
    return obj
end
```

여기서 중요한 관찰은 이 역방향 분석이 사용-정의 체인을 따라 자연스럽게 탈출 정보를 흐르게 한다는 것입니다[^BackandForth]. 결과적으로 이 방식은 탈출 분석의 간단한 구현을 가능하게 하며, 예를 들어 `PhiNode`는 `PhiNode`에 부과된 탈출 정보를 그 선행 값으로 전파함으로써 간단하게 처리할 수 있습니다:

```@repl EAUtils
code_escapes((Bool, String, String)) do cnd, s, t
    if cnd
        obj = Ref(s)
    else
        obj = Ref(t)
    end
    return obj
end
```

### [Alias Analysis](@id EA-Alias-Analysis)

`EscapeAnalysis`는 특정 정확도로 객체 필드에 부과된 탈출에 대해 추론하기 위해 역방향 필드 분석을 구현하며, `x::EscapeInfo`의 `x.AliasInfo` 속성은 이 목적을 위해 존재합니다. 이는 "사용" 지점에서 `x`의 필드에 별칭을 가질 수 있는 모든 가능한 값을 기록하고, 이후 "정의" 지점에서 해당 기록된 값의 탈출 정보를 실제 필드 값으로 전파합니다. 보다 구체적으로, 이 분석은 `getfield` 호출을 분석하여 객체의 필드에 별칭을 가질 수 있는 값을 기록하고, 이후 `%new(...)` 표현식이나 `setfield!` 호출을 분석할 때 해당 필드로 탈출 정보를 전파합니다[^Dynamism].

```@repl EAUtils
code_escapes((String,)) do s
    obj = SafeRef("init")
    obj[] = s
    v = obj[]
    return v
end
```

위의 예에서 `%3`(해당하는 `v`)에 적용된 `ReturnEscape`는 `%1`(해당하는 `obj`)에 직접 전파되지 않고, 오히려 `ReturnEscape`는 `_2`(해당하는 `s`)에만 전파됩니다. 여기서 `%3`은 `%1`의 `AliasInfo` 속성에 기록되며, 이는 `%1`의 첫 번째 필드에 별칭을 가질 수 있기 때문입니다. 그리고 `Base.setfield!(%1, :x, _2)::String`을 분석할 때, 그 탈출 정보는 `_2`로 전파되지만 `%1`에는 전파되지 않습니다.

그래서 `EscapeAnalysis`는 객체 필드의 탈출을 분석하기 위해 `getfield`-`%new`/`setfield!` 체인에서 어떤 IR 요소가 별칭될 수 있는지를 추적합니다. 하지만 실제로 이 별칭 분석은 다른 IR 요소를 처리할 수 있도록 일반화되어야 합니다. 이는 Julia IR에서 동일한 객체가 때때로 서로 다른 IR 요소로 표현되기 때문에, 실제로 동일한 객체를 나타낼 수 있는 서로 다른 IR 요소가 동일한 탈출 정보를 공유하도록 해야 하기 때문입니다. 피연산자로서 동일한 객체를 반환하는 IR 요소, 예를 들어 `PiNode`와 `typeassert`는 IR 수준의 별칭을 유발할 수 있으며, 따라서 이러한 별칭된 값들 간에 공유되어야 하는 탈출 정보가 필요합니다. 더 흥미롭게도, 이는 `PhiNode`에 대한 변형을 올바르게 추론하는 데에도 필요합니다. 다음 예제를 살펴보겠습니다:

```@repl EAUtils
code_escapes((Bool, String,)) do cond, x
    if cond
        ϕ2 = ϕ1 = SafeRef("foo")
    else
        ϕ2 = ϕ1 = SafeRef("bar")
    end
    ϕ2[] = x
    y = ϕ1[]
    return y
end
```

`ϕ1 = %5`와 `ϕ2 = %6`는 별칭이므로 `ReturnEscape`가 `%8 = Base.getfield(%6, :x)::String` (즉, `y = ϕ1[]`에 해당)에서 `%5, :x, _3::String` (즉, `ϕ2[] = x`에 해당)으로 전파되어야 합니다. 이러한 탈출 정보가 올바르게 전파되기 위해서는 분석이 `ϕ1`과 `ϕ2`의 *선행자*도 별칭이 될 수 있음을 인식하고 그들의 탈출 정보를 동등하게 만들어야 합니다.

이러한 별칭 정보의 흥미로운 속성 중 하나는 "사용" 사이트에서 알 수 없지만 "정의" 사이트에서만 유도될 수 있다는 것입니다(별칭은 개념적으로 할당과 동등하기 때문에). 따라서 이는 자연스럽게 역방향 분석에 적합하지 않습니다. 관련 값 간의 탈출 정보를 효율적으로 전파하기 위해, EscapeAnalysis.jl은 오래된 JVM 논문[^JVM05]에서 설명된 탈출 분석 알고리즘에서 영감을 받은 접근 방식을 사용합니다. 즉, 탈출 격자 요소를 관리하는 것 외에도, 분석은 "동등한" 별칭 집합을 유지하며, 이는 별칭이 있는 인수와 SSA 문장의 분리된 집합입니다. 별칭 집합은 서로 별칭이 될 수 있는 값을 관리하고, 이러한 별칭 값 중 어떤 것에 부과된 탈출 정보를 서로 동등하게 만들 수 있도록 합니다.

### [Array Analysis](@id EA-Array-Analysis)

위에서 설명한 객체 필드에 대한 별칭 분석은 배열 작업을 분석하는 데에도 일반화될 수 있습니다. `EscapeAnalysis`는 다양한 원시 배열 작업을 처리하여 `arrayref`-`arrayset` 사용-정의 체인을 통해 탈출을 전파하고 할당된 배열이 너무 보수적으로 탈출하지 않도록 구현합니다:

```@repl EAUtils
code_escapes((String,)) do s
    ary = Any[]
    push!(ary, SafeRef(s))
    return ary[1], length(ary)
end
```

위의 예제에서 `EscapeAnalysis`는 `%20`과 `%2`(할당된 객체 `SafeRef(s)`에 해당)가 `arrayset`-`arrayref` 체인을 통해 별칭이 있음을 이해하고 이들에 대해 `ReturnEscape`를 부과하지만, 할당된 배열 `%1`( `ary`에 해당)에는 이를 부과하지 않습니다. `EscapeAnalysis`는 여전히 `ary`에 대해 `ThrownEscape`를 부과하는데, 이는 `BoundsError`를 통해 발생할 수 있는 잠재적 탈출을 고려해야 하기 때문입니다. 그러나 최적화할 때 이러한 처리되지 않은 `ThrownEscape`는 종종 무시될 수 있다는 점도 주목해야 합니다.

또한 배열 인덱스 정보와 배열 차원을 *정확하게* 알 수 있는 경우, `EscapeAnalysis`는 `arrayref`-`arrayset` 체인을 통해 "요소별" 별칭에 대해서도 추론할 수 있으며, `EscapeAnalysis`는 객체에 대해 "필드별" 별칭 분석을 수행합니다:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Vector{Any}(undef, 2)
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

`ReturnEscape`는 `%2`(즉, `SafeRef(s)`)에만 적용되며 `%4`(즉, `SafeRef(t)`)에는 적용되지 않는다는 점에 유의하십시오. 이는 할당된 배열의 차원과 모든 `arrayref`/`arrayset` 작업에 관련된 인덱스가 상수 정보로 제공되며, `EscapeAnalysis`가 `%6`이 `%2`에 별칭이 있지만 `%4`에는 절대 별칭이 없다는 것을 이해할 수 있기 때문입니다. 이러한 경우, 후속 최적화 패스는 `Base.arrayref(true, %1, 1)::Any`를 `%2`(즉, "로드 포워딩")로 대체할 수 있으며, 궁극적으로 배열 `%1`의 할당을 완전히 제거할 수 있습니다(즉, "스칼라 대체").

객체 필드 분석과 비교할 때, 객체 필드에 대한 접근은 추론에 의해 파생된 타입 정보를 사용하여 간단하게 분석할 수 있지만, 배열 차원은 타입 정보로 인코딩되지 않으므로 해당 정보를 도출하기 위해 추가 분석이 필요합니다. `EscapeAnalysis`는 현재 할당된 배열의 차원을 분석하기 위해 추가적인 간단한 선형 스캔을 먼저 수행한 후, 주요 분석 루틴을 시작하여 후속 탈출 분석이 해당 배열에 대한 작업을 정확하게 분석할 수 있도록 합니다.

그러나 이러한 정밀한 "요소별" 별칭 분석은 종종 어렵습니다. 본질적으로 배열에 내재된 주요 어려움은 배열의 차원과 인덱스가 종종 비상수라는 점입니다:

  * 루프는 종종 루프 변형, 비상수 배열 인덱스를 생성합니다.
  * (벡터에 특정) 배열 크기 조정은 배열 차원을 변경하고 그 상수성을 무효화합니다.

구체적인 예를 통해 그 어려움에 대해 논의해 봅시다.

다음 예에서 `EscapeAnalysis`는 `Base.arrayset(false, %4, %8, %6)::Vector{Any}`의 인덱스가 (자명하게) 상수가 아니기 때문에 정확한 별칭 분석에 실패합니다. 특히 `Any[nothing, nothing]`는 루프를 형성하고 `%6`이 제어 흐름에 의존하는 값인 ϕ-노드 값으로 표현되는 루프에서 해당 `arrayset` 작업을 호출합니다. 결과적으로 `ReturnEscape`는 `%23`(해당하는 `SafeRef(s)`)와 `%25`(해당하는 `SafeRef(t)`) 모두에 부과되지만, 이상적으로는 `%23`에만 부과되고 `%25`에는 부과되지 않기를 원합니다.

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[nothing, nothing]
    ary[1] = SafeRef(s)
    ary[2] = SafeRef(t)
    return ary[1], length(ary)
end
```

다음 예시는 벡터 크기 조정이 정밀한 별칭 분석을 어렵게 만드는 방법을 보여줍니다. 본질적인 어려움은 할당된 배열 `%1`의 차원이 처음에 `0`으로 초기화되지만, 이후 두 번의 `:jl_array_grow_end` 호출로 인해 변경된다는 것입니다. 현재 `EscapeAnalysis`는 배열 크기 조정 작업을 만날 때마다 정밀한 별칭 분석을 포기하며, 따라서 `%2`( `SafeRef(s)`에 해당)와 `%20`( `SafeRef(t)`에 해당) 모두에 대해 `ReturnEscape`가 적용됩니다:

```@repl EAUtils
code_escapes((String,String)) do s, t
    ary = Any[]
    push!(ary, SafeRef(s))
    push!(ary, SafeRef(t))
    ary[1], length(ary)
end
```

이러한 어려움을 해결하기 위해, 우리는 추론이 배열 차원을 인식하고 흐름에 민감한 방식으로 배열 차원을 전파할 수 있도록 해야 하며[^ArrayDimension], 루프 변동 값의 멋진 표현을 고안해야 합니다.

`EscapeAnalysis`는 현재 배열 차원이나 인덱스가 자명하게 비상수일 때, 정확한 인덱스 정보를 추적하지 않는 더 부정확한 분석으로 빠르게 전환됩니다. 이 전환은 데이터 흐름 분석 프레임워크에서 `EscapeInfo.AliasInfo` 속성의 격자 조인 연산으로 자연스럽게 구현될 수 있습니다.

### [Exception Handling](@id EA-Exception-Handling)

`EscapeAnalysis`가 예외를 통해 발생할 수 있는 탈출을 어떻게 처리하는지 주목할 가치가 있습니다. 단순히 `try` 블록에서 발생할 수 있는 모든 값에 대해 `:the_exception` 객체에 부과된 탈출 정보를 전파하는 것으로 충분해 보입니다. 그러나 실제로는 `Base.current_exceptions` 및 `rethrow`와 같은 여러 다른 방법으로 Julia에서 예외 객체에 접근할 수 있습니다. 예를 들어, 탈출 분석은 아래 예제에서 `r`의 잠재적 탈출을 고려해야 합니다:

```@repl EAUtils
const GR = Ref{Any}();
@noinline function rethrow_escape!()
    try
        rethrow()
    catch err
        GR[] = err
    end
end;
get′(x) = isassigned(x) ? x[] : throw(x);

code_escapes() do
    r = Ref{String}()
    local t
    try
        t = get′(r)
    catch err
        t = typeof(err)   # `err` (which `r` aliases to) doesn't escape here
        rethrow_escape!() # but `r` escapes here
    end
    return t
end
```

모든 가능한 예외 인터페이스를 통해 올바르게 탈출할 수 있는 방법을 추론하기 위해서는 전반적인 분석이 필요합니다. 현재로서는 모든 잠재적으로 발생할 수 있는 객체에 대해 가장 상위의 탈출 정보를 보수적으로 전파하고 있습니다. 이는 예외 처리와 오류 경로가 일반적으로 성능에 민감할 필요가 없기 때문에 추가 분석을 수행하는 것이 그리 가치가 없을 수 있기 때문입니다. 또한 오류 경로의 최적화는 종종 지연 시간 문제로 인해 의도적으로 "비최적화"되어 있기 때문에 매우 비효율적일 수 있습니다.

`x::EscapeInfo`의 `x.ThrownEscape` 속성은 `x`가 예외로 던져질 수 있는 SSA 문을 기록합니다. 이 정보를 사용하여 `EscapeAnalysis`는 각 `try` 영역에서 던져질 수 있는 예외에 한정하여 가능한 탈출을 제한적으로 전파할 수 있습니다:

```@repl EAUtils
result = code_escapes((String,String)) do s1, s2
    r1 = Ref(s1)
    r2 = Ref(s2)
    local ret
    try
        s1 = get′(r1)
        ret = sizeof(s1)
    catch err
        global GV = err # will definitely escape `r1`
    end
    s2 = get′(r2)       # still `r2` doesn't escape fully
    return s2
end
```

## Analysis Usage

`analyze_escapes`는 SSA-IR 요소의 탈출 정보를 분석하는 진입점입니다.

대부분의 최적화는 SROA(`sroa_pass!`)와 같이 인라인 패스(`ssa_inlining_pass!`)가 절차 간 호출을 해결하고 호출자 소스를 확장하여 최적화된 소스에 적용될 때 더 효과적입니다. 따라서 `analyze_escapes`는 인라인 후 IR을 분석하고 특정 메모리 관련 최적화에 유용한 탈출 정보를 수집할 수 있습니다.

그러나 인라인과 같은 특정 최적화 패스는 제어 흐름을 변경하고 죽은 코드를 제거할 수 있기 때문에, 이들은 탈출 정보의 절차 간 유효성을 깨뜨릴 수 있습니다. 특히, 절차 간 유효한 탈출 정보를 수집하기 위해서는 인라인 이전의 IR을 분석해야 합니다.

이러한 이유로 `analyze_escapes`는 모든 Julia 수준 최적화 단계에서 `IRCode`를 분석할 수 있으며, 특히 다음 두 단계에서 사용될 것으로 예상됩니다:

  * `IPO EA`: 사전 인라인 IR을 분석하여 IPO 유효 탈출 정보 캐시를 생성합니다.
  * `Local EA`: 포스트 인라인 IR을 분석하여 지역적으로 유효한 탈출 정보를 수집합니다.

`IPO EA`에서 파생된 탈출 정보는 `ArgEscapeCache` 데이터 구조로 변환되어 전역적으로 캐시됩니다. 적절한 `get_escape_cache` 콜백을 `analyze_escapes`에 전달함으로써, 탈출 분석은 이전 `IPO EA`에 의해 파생된 비인라인 호출자의 캐시된 절차 간 정보를 활용하여 분석 정확도를 향상시킬 수 있습니다. 더 흥미로운 점은, `IPO EA` 탈출 정보를 타입 추론에 사용하는 것도 유효하다는 것입니다. 예를 들어, 가변 객체의 `Const`/`PartialStruct`/`MustAlias`를 형성함으로써 추론 정확도를 향상시킬 수 있습니다.

```@docs
Core.Compiler.EscapeAnalysis.analyze_escapes
Core.Compiler.EscapeAnalysis.EscapeState
Core.Compiler.EscapeAnalysis.EscapeInfo
```

---

[^LatticeDesign]: Our type inference implementation takes the alternative approach, where each lattice property is represented by a special lattice element type object. It turns out that it started to complicate implementations of the lattice operations mainly because it often requires conversion rules between each lattice element type object. And we are working on [overhauling our type inference lattice implementation](https://github.com/JuliaLang/julia/pull/42596) with `EscapeInfo`-like lattice design.

[^MM02]: *A Graph-Free approach to Data-Flow Analysis*.      Markas Mohnen, 2002, April.      [https://api.semanticscholar.org/CorpusID:28519618](https://api.semanticscholar.org/CorpusID:28519618).

[^BackandForth]: Our type inference algorithm in contrast is implemented as a forward analysis, because type information usually flows from "definition" to "usage" and it is more natural and effective to propagate such information in a forward way.

[^Dynamism]: In some cases, however, object fields can't be analyzed precisely. For example, object may escape to somewhere `EscapeAnalysis` can't account for possible memory effects on it, or fields of the objects simply can't be known because of the lack of type information. In such cases `AliasInfo` property is raised to the topmost element within its own lattice order, and it causes succeeding field analysis to be conservative and escape information imposed on fields of an unanalyzable object to be propagated to the object itself.

[^JVM05]: *Escape Analysis in the Context of Dynamic Compilation and Deoptimization*.       Thomas Kotzmann and Hanspeter Mössenböck, 2005, June.       [https://dl.acm.org/doi/10.1145/1064979.1064996](https://dl.acm.org/doi/10.1145/1064979.1064996).

[^ArrayDimension]: Otherwise we will need yet another forward data-flow analysis on top of the escape analysis.
