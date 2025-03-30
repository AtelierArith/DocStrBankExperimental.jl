# [Performance Tips](@id man-performance-tips)

다음 섹션에서는 Julia 코드가 가능한 한 빠르게 실행되도록 도와줄 수 있는 몇 가지 기술을 간략하게 살펴보겠습니다.

## Performance critical code should be inside a function

성능이 중요한 코드는 함수 안에 있어야 합니다. 함수 내부의 코드는 Julia의 컴파일러 작동 방식 때문에 최상위 코드보다 훨씬 빠르게 실행되는 경향이 있습니다.

함수의 사용은 성능뿐만 아니라 중요합니다: 함수는 더 재사용 가능하고 테스트 가능하며, 어떤 단계가 수행되고 있는지, 그 입력과 출력이 무엇인지 명확하게 합니다. [Write functions, not just scripts](@ref)는 또한 줄리아 스타일 가이드의 권장 사항입니다.

함수는 전역 변수에 직접 작용하는 대신 인수를 받아야 합니다. 다음 사항을 참조하십시오.

## Avoid untyped global variables

타입이 지정되지 않은 전역 변수의 값은 언제든지 변경될 수 있으며, 이로 인해 그 타입이 변경될 수 있습니다. 이는 컴파일러가 전역 변수를 사용하는 코드를 최적화하는 데 어려움을 줍니다. 이는 타입 값 변수가 있는 경우에도 적용됩니다. 즉, 전역 수준의 타입 별칭에 해당합니다. 변수는 가능한 한 로컬로 유지하거나 함수에 인수로 전달해야 합니다.

우리는 전역 이름이 자주 상수임을 발견했으며, 이를 그렇게 선언하면 성능이 크게 향상된다는 것을 알게 되었습니다:

```julia
const DEFAULT_VAL = 0
```

글로벌이 항상 동일한 유형으로 알려져 있다면, [the type should be annotated](@ref man-typed-globals).

사용되지 않은 전역 변수의 사용은 사용 지점에서 그들의 타입을 주석으로 달아 최적화할 수 있습니다:

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

함수에 인수를 전달하는 것은 더 나은 스타일입니다. 이는 더 재사용 가능한 코드를 생성하고 입력과 출력이 무엇인지 명확하게 합니다.

!!! note
    REPL의 모든 코드는 전역 범위에서 평가되므로, 최상위에서 정의되고 할당된 변수는 **전역** 변수가 됩니다. 모듈 내의 최상위 범위에서 정의된 변수도 전역입니다.


다음 REPL 세션에서:

```julia-repl
julia> x = 1.0
```

다음과 같습니다:

```julia-repl
julia> global x = 1.0
```

따라서 이전에 논의된 모든 성능 문제들이 적용됩니다.

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

성능을 측정하는 데 유용한 도구는 [`@time`](@ref) 매크로입니다. 여기서 우리는 위의 전역 변수를 사용한 예제를 반복하지만, 이번에는 타입 주석이 제거되었습니다:

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

첫 번째 호출(`@time sum_global()`)에서 함수가 컴파일됩니다. (이번 세션에서 [`@time`](@ref)를 아직 사용하지 않았다면, 타이밍에 필요한 함수도 컴파일됩니다.) 이 실행의 결과를 진지하게 받아들여서는 안 됩니다. 두 번째 실행에서는 시간을 보고하는 것 외에도 상당량의 메모리가 할당되었다고 표시됩니다. 우리는 여기서 64비트 부동 소수점 벡터의 모든 요소에 대한 합계를 계산하고 있으므로 (힙) 메모리를 할당할 필요가 없어야 합니다.

`@time`이 보고하는 것은 구체적으로 *힙* 할당이라는 점을 명확히 해야 합니다. 이는 일반적으로 가변 객체나 가변 크기 컨테이너(예: `Array` 또는 `Dict`, 문자열, 또는 런타임에만 유형이 알려지는 "유형 불안정" 객체)를 생성하거나 성장시키기 위해 필요합니다. 이러한 메모리 블록을 할당(또는 해제)하는 것은 libc에 대한 비용이 많이 드는 함수 호출(예: C의 `malloc`를 통해)을 요구할 수 있으며, 가비지 수집을 위해 추적되어야 합니다. 반면, 숫자(빅넘 제외), 튜플 및 불변 `struct`와 같은 불변 값은 스택이나 CPU 레지스터 메모리와 같이 훨씬 더 저렴하게 저장될 수 있으므로, 일반적으로 "할당"하는 것의 성능 비용에 대해 걱정하지 않습니다.

예상치 못한 메모리 할당은 거의 항상 코드에 문제가 있다는 신호이며, 일반적으로는 타입 안정성 문제나 많은 작은 임시 배열을 생성하는 문제입니다. 따라서 할당 자체 외에도, 귀하의 함수에 대해 생성된 코드가 최적에서 멀리 떨어져 있을 가능성이 매우 높습니다. 이러한 징후를 진지하게 받아들이고 아래의 조언을 따르십시오.

이 특정 경우에 메모리 할당은 타입이 불안정한 전역 변수 `x`의 사용으로 인해 발생하므로, 대신 `x`를 함수의 인수로 전달하면 더 이상 메모리를 할당하지 않으며(아래에 보고된 나머지 할당은 전역 범위에서 `@time` 매크로를 실행한 결과입니다) 첫 번째 호출 이후에는 상당히 빨라집니다:

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

전역 범위에서 `@time` 매크로를 실행한 결과로 보이는 1개의 할당이 있습니다. 대신 함수를 사용하여 타이밍을 실행하면 실제로 할당이 수행되지 않음을 확인할 수 있습니다:

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

일부 상황에서는 함수가 작업의 일환으로 메모리를 할당해야 할 수 있으며, 이로 인해 위의 간단한 그림이 복잡해질 수 있습니다. 이러한 경우, 문제를 진단하기 위해 아래의 [tools](@ref tools) 중 하나를 사용하거나, 할당을 알고리즘적 측면과 분리하는 함수 버전을 작성하는 것을 고려하십시오(참조: [Pre-allocating outputs](@ref)).

!!! note
    보다 심각한 벤치마킹을 위해 [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) 패키지를 고려해 보세요. 이 패키지는 여러 번 함수를 평가하여 노이즈를 줄이는 등의 기능을 제공합니다.


## [Tools](@id tools)

Julia와 그 패키지 생태계에는 문제를 진단하고 코드 성능을 향상시키는 데 도움이 될 수 있는 도구가 포함되어 있습니다:

  * [Profiling](@ref)는 실행 중인 코드의 성능을 측정하고 병목 현상으로 작용하는 줄을 식별할 수 있게 해줍니다. 복잡한 프로젝트의 경우, [ProfileView](https://github.com/timholy/ProfileView.jl) 패키지가 프로파일링 결과를 시각화하는 데 도움을 줄 수 있습니다.
  * [JET](https://github.com/aviatesk/JET.jl) 패키지는 코드에서 일반적인 성능 문제를 찾는 데 도움을 줄 수 있습니다.
  * 예상치 못한 대규모 메모리 할당은 [`@time`](@ref), [`@allocated`](@ref) 또는 프로파일러(가비지 수집 루틴 호출을 통해)에서 보고된 바와 같이 코드에 문제가 있을 수 있음을 암시합니다. 할당에 대한 다른 이유가 보이지 않으면 타입 문제를 의심하십시오. 또한 `--track-allocation=user` 옵션으로 Julia를 시작하고 결과 `*.mem` 파일을 검사하여 이러한 할당이 발생하는 위치에 대한 정보를 확인할 수 있습니다. [Memory allocation analysis](@ref)를 참조하십시오.
  * `@code_warntype`는 코드의 표현을 생성하여 타입 불확실성을 초래하는 표현을 찾는 데 유용할 수 있습니다. 아래의 [`@code_warntype`](@ref)를 참조하세요.

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

매개변수화된 유형, 배열을 포함하여 작업할 때는 가능한 경우 추상 유형으로 매개변수화하는 것을 피하는 것이 가장 좋습니다.

다음 사항을 고려하십시오:

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

`a`는 추상 타입 [`Real`](@ref)의 배열이기 때문에, 모든 `Real` 값을 담을 수 있어야 합니다. `Real` 객체는 임의의 크기와 구조를 가질 수 있으므로, `a`는 개별적으로 할당된 `Real` 객체에 대한 포인터 배열로 표현되어야 합니다. 그러나 대신 같은 타입의 숫자만 저장하도록 허용한다면, 예를 들어 [`Float64`](@ref), `a`에 저장할 수 있는 숫자는 더 효율적으로 저장될 수 있습니다:

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

`a`에 숫자를 할당하면 이제 이를 `Float64`로 변환하며, `a`는 효율적으로 조작할 수 있는 64비트 부동 소수점 값의 연속 블록으로 저장됩니다.

컨테이너에서 추상 값 유형을 피할 수 없다면, 런타임 타입 검사를 피하기 위해 `Any`로 매개변수를 설정하는 것이 때때로 더 나을 수 있습니다. 예를 들어, `IdDict{Any, Any}`는 `IdDict{Type, Vector}`보다 성능이 더 좋습니다.

또한 [Parametric Types](@ref) 아래의 논의를 참조하십시오.

## Type declarations

많은 선택적 타입 선언이 있는 언어에서, 선언을 추가하는 것이 코드를 더 빠르게 실행하는 주요 방법입니다. 그러나 이는 줄리아에서는 *아닙니다*. 줄리아에서는 컴파일러가 일반적으로 모든 함수 인수, 지역 변수 및 표현식의 타입을 알고 있습니다. 그러나 선언이 유용한 몇 가지 특정 사례가 있습니다.

### Avoid fields with abstract type

필드의 타입을 지정하지 않고도 타입을 선언할 수 있습니다:

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

이것은 `a`가 어떤 타입이든 가능하게 합니다. 이는 종종 유용할 수 있지만 단점도 있습니다: `MyAmbiguousType` 타입의 객체에 대해서는 컴파일러가 고성능 코드를 생성할 수 없습니다. 그 이유는 컴파일러가 객체의 값을 아니라 타입을 사용하여 코드를 빌드하는 방법을 결정하기 때문입니다. 불행히도, `MyAmbiguousType` 타입의 객체에 대해 추론할 수 있는 것은 매우 적습니다:

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

`b`와 `c`의 값은 같은 유형이지만, 메모리에서의 데이터 기본 표현은 매우 다릅니다. 필드 `a`에 숫자 값만 저장하더라도, [`UInt8`](@ref)의 메모리 표현이 [`Float64`](@ref)와 다르다는 사실은 CPU가 이를 두 가지 다른 종류의 명령어로 처리해야 함을 의미합니다. 필요한 정보가 유형에 없기 때문에, 이러한 결정은 실행 시간에 내려져야 합니다. 이는 성능을 저하시킵니다.

`a`의 타입을 선언함으로써 더 나은 결과를 얻을 수 있습니다. 여기서는 `a`가 여러 타입 중 하나일 수 있는 경우에 집중하고 있으며, 이 경우 자연스러운 해결책은 매개변수를 사용하는 것입니다. 예를 들어:

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

이것은 다음보다 더 나은 선택입니다.

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

첫 번째 버전은 래퍼 객체의 유형에서 `a`의 유형을 지정하기 때문입니다. 예를 들어:

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

필드 `a`의 유형은 `m`의 유형에서 쉽게 결정할 수 있지만, `t`의 유형에서는 그렇지 않습니다. 실제로 `t`에서는 필드 `a`의 유형을 변경할 수 있습니다:

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

대조적으로, `m`이 생성된 후에는 `m.a`의 타입이 변경될 수 없습니다:

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

`m`의 타입에서 `m.a`의 타입이 알려진다는 사실과 함수 중간에 타입이 변경될 수 없다는 사실은 컴파일러가 `m`과 같은 객체에 대해 고도로 최적화된 코드를 생성할 수 있게 해주지만, `t`와 같은 객체에 대해서는 그렇지 않다는 것을 의미합니다.

물론, 이것은 우리가 `m`을 구체적인 타입으로 구성할 때만 참입니다. 우리는 이를 추상 타입으로 명시적으로 구성함으로써 깨뜨릴 수 있습니다:

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

모든 실용적인 목적을 위해, 이러한 객체는 `MyStillAmbiguousType`의 객체와 동일하게 동작합니다.

간단한 함수에 대해 생성된 코드의 양을 비교하는 것은 매우 유익합니다.

```julia
func(m::MyType) = m.a+1
```

사용하여

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

길이 문제로 인해 결과는 여기에서 표시되지 않지만, 직접 시도해 볼 수 있습니다. 첫 번째 경우에 타입이 완전히 지정되어 있기 때문에, 컴파일러는 런타임에 타입을 해결하기 위해 코드를 생성할 필요가 없습니다. 이로 인해 코드가 더 짧고 빠르게 실행됩니다.

완전히 매개변수화되지 않은 타입은 추상 타입처럼 동작한다는 점도 염두에 두어야 한다. 예를 들어, 완전히 지정된 `Array{T,n}`는 구체적이지만, 매개변수가 주어지지 않은 `Array` 자체는 구체적이지 않다:

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

이 경우, `MyType`을 필드 `a::Array`로 선언하는 것보다 필드를 `a::Array{T,N}` 또는 `a::A`로 선언하는 것이 더 좋습니다. 여기서 `{T,N}` 또는 `A`는 `MyType`의 매개변수입니다.

구조체의 필드가 함수이거나 더 일반적으로 호출 가능한 객체로 의도된 경우, 이전의 조언은 특히 유용합니다. 구조체를 다음과 같이 정의하는 것은 매우 유혹적입니다:

```julia
struct MyCallableWrapper
    f::Function
end
```

하지만 `Function`이 추상 타입이기 때문에, `wrapper.f`에 대한 모든 호출은 필드 `f`에 접근하는 타입 불안정성 때문에 동적 디스패치를 요구합니다. 대신, 다음과 같은 코드를 작성해야 합니다:

```julia
struct MyCallableWrapper{F}
    f::F
end
```

거의 동일한 동작을 하지만 훨씬 더 빠릅니다(타입 불안정성이 제거되기 때문입니다). `F<:Function`을 강제하지 않음을 유의하세요: 이는 `Function`의 하위 유형이 아닌 호출 가능한 객체도 필드 `f`에 허용된다는 것을 의미합니다.

### Avoid fields with abstract containers

컨테이너 유형에도 동일한 모범 사례가 적용됩니다:

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

예를 들어:

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

`MySimpleContainer`의 경우, 객체는 그 타입과 매개변수에 의해 완전히 지정되므로, 컴파일러는 최적화된 함수를 생성할 수 있습니다. 대부분의 경우, 이것으로 충분할 것입니다.

컴파일러가 이제 완벽하게 작업을 수행할 수 있지만, 경우에 따라 *당신*이 `a`의 *요소 유형*에 따라 코드가 다른 작업을 수행하기를 원할 수 있습니다. 일반적으로 이를 달성하는 가장 좋은 방법은 특정 작업(여기서는 `foo`)을 별도의 함수로 감싸는 것입니다:

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

이것은 모든 경우에 컴파일러가 최적화된 코드를 생성할 수 있도록 하면서 사안을 간단하게 유지합니다.

그러나 `MySimpleContainer`의 필드 `a`의 서로 다른 요소 유형 또는 `AbstractVector` 유형에 대해 외부 함수의 서로 다른 버전을 선언해야 할 경우가 있습니다. 다음과 같이 할 수 있습니다:

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

데이터 구조가 어떤 유형의 값을 포함할 수 있는 경우(예: `Array{Any}` 유형의 배열) 작업하는 것이 종종 편리합니다. 그러나 이러한 구조 중 하나를 사용하고 있고 요소의 유형을 알고 있다면, 이 정보를 컴파일러와 공유하는 것이 도움이 됩니다:

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

여기서 우리는 `a`의 첫 번째 요소가 [`Int32`](@ref)일 것이라는 것을 알게 되었습니다. 이렇게 주석을 다는 것은 값이 예상된 유형이 아닐 경우 런타임 오류를 발생시켜 특정 버그를 더 일찍 잡을 수 있는 추가적인 이점이 있습니다.

`a[1]`의 타입이 정확히 알려지지 않은 경우, `x`는 `x = convert(Int32, a[1])::Int32`를 통해 선언될 수 있습니다. [`convert`](@ref) 함수를 사용하면 `a[1]`이 `Int32`로 변환 가능한 모든 객체(예: `UInt8`)가 될 수 있으므로, 타입 요구 사항을 완화하여 코드의 일반성을 높입니다. 이 맥락에서 `convert` 자체가 타입 안정성을 달성하기 위해 타입 주석이 필요하다는 점에 유의하세요. 이는 컴파일러가 모든 함수 인수의 타입이 알려지지 않는 한, 함수의 반환값의 타입을 유추할 수 없기 때문입니다.

타입 주석은 타입이 추상적이거나 런타임에 생성되는 경우 성능을 향상시키지 않으며(실제로 성능을 저하시킬 수 있음) 이는 컴파일러가 주석을 사용하여 후속 코드를 특수화할 수 없기 때문입니다. 또한 타입 검사가 자체적으로 시간을 소모합니다. 예를 들어, 코드에서:

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

`c`의 주석은 성능에 해를 끼칩니다. 런타임에 생성된 타입을 포함하는 성능 좋은 코드를 작성하려면 아래에서 논의된 [function-barrier technique](@ref kernel-functions)를 사용하고, 생성된 타입이 커널 함수의 인수 타입 중에 나타나도록 하여 커널 연산이 컴파일러에 의해 적절하게 특수화되도록 해야 합니다. 예를 들어, 위의 코드 조각에서 `b`가 생성되자마자, 다른 함수 `k`, 즉 커널에 전달될 수 있습니다. 예를 들어, 함수 `k`가 `b`를 타입 매개변수 `T`의 인수로 `Complex{T}` 타입으로 선언하면, `k` 내의 할당문에서 다음과 같은 형태의 타입 주석이 나타납니다:

```julia
c = (b + 1.0f0)::Complex{T}
```

성능에 방해가 되지 않지만 (도움이 되지도 않음) 컴파일러가 `k`가 컴파일될 때 `c`의 타입을 결정할 수 있기 때문입니다.

### Be aware of when Julia avoids specializing

휴리스틱으로, Julia는 세 가지 특정 경우인 `Type`, `Function`, `Vararg`에서 인수 유형 매개변수에 대해 자동으로 [specializing](@ref man-method-specializations)를 피합니다. Julia는 인수가 메서드 내에서 사용될 때 항상 특수화하지만, 인수가 다른 함수로 단순히 전달될 경우에는 그렇지 않습니다. 이는 일반적으로 런타임에서 성능에 영향을 미치지 않으며 [improves compiler performance](@ref compiler-efficiency-issues)입니다. 만약 귀하의 경우 런타임에서 성능에 영향을 미친다면, 메서드 선언에 유형 매개변수를 추가하여 특수화를 유도할 수 있습니다. 다음은 몇 가지 예입니다:

이것은 전문화되지 않을 것입니다:

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

하지만 이것은:

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

이들은 전문화되지 않을 것입니다:

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

하지만 이것은:

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

이것은 전문화되지 않을 것입니다:

```julia
f_vararg(x::Int...) = tuple(x...)
```

하지만 이것은:

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

하나의 유형 매개변수만 도입하면 다른 유형이 제약이 없더라도 특수화를 강제할 수 있습니다. 예를 들어, 이것도 특수화되며 인수가 모두 동일한 유형이 아닐 때 유용합니다:

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

[`@code_typed`](@ref)와 친구들은 항상 전문화된 코드를 보여줍니다. 비록 Julia가 일반적으로 그 메서드 호출을 전문화하지 않더라도 말입니다. 인수 유형이 변경될 때 전문화가 생성되는지 확인하려면 [method internals](@ref ast-lowered-method)를 확인해야 합니다. 즉, `Base.specializations(@which f(...))`가 문제의 인수에 대한 전문화를 포함하는지 확인해야 합니다.

## Break functions into multiple definitions

함수를 많은 작은 정의로 작성하면 컴파일러가 가장 적합한 코드를 직접 호출하거나 심지어 인라인할 수 있습니다.

여기 여러 정의로 작성해야 하는 "복합 함수"의 예가 있습니다:

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

이것은 더 간결하고 효율적으로 다음과 같이 작성될 수 있습니다:

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

그러나 `mynorm` 예제와 같이 작성된 코드에서 컴파일러가 죽은 분기를 최적화하는 데 매우 효율적이라는 점은 주목해야 합니다.

## Write "type-stable" functions

가능한 경우, 함수가 항상 동일한 유형의 값을 반환하도록 보장하는 것이 도움이 됩니다. 다음 정의를 고려해 보십시오:

```julia
pos(x) = x < 0 ? 0 : x
```

비록 이것이 충분히 무해해 보이지만, 문제는 `0`이 정수(`Int` 타입)이고 `x`는 어떤 타입일 수 있다는 것입니다. 따라서 `x`의 값에 따라 이 함수는 두 가지 타입 중 하나의 값을 반환할 수 있습니다. 이러한 동작은 허용되며, 경우에 따라 바람직할 수 있습니다. 그러나 다음과 같이 쉽게 수정할 수 있습니다:

```julia
pos(x) = x < 0 ? zero(x) : x
```

[`oneunit`](@ref) 함수와 더 일반적인 [`oftype(x, y)`](@ref) 함수가 있습니다. 이 함수는 `y`를 `x`의 타입으로 변환하여 반환합니다.

## Avoid changing the type of a variable

함수 내에서 반복적으로 사용되는 변수에 대해 유사한 "타입 안정성" 문제가 존재합니다:

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

로컬 변수 `x`는 정수로 시작하고, 한 번의 루프 반복 후에 부동 소수점 숫자가 됩니다(결과는 [`/`](@ref) 연산자). 이로 인해 컴파일러가 루프 본체를 최적화하기가 더 어려워집니다. 몇 가지 가능한 수정 방법이 있습니다:

  * `x`를 `x = 1.0`으로 초기화합니다.
  * `x::Float64 = 1`
  * `x = oneunit(Float64)`의 명시적 변환을 사용하세요.
  * 초기화는 첫 번째 루프 반복으로 `x = 1 / rand()`로 하고, 그 다음 `for i = 2:10` 루프를 실행합니다.

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

많은 함수는 일부 설정 작업을 수행한 다음, 핵심 계산을 수행하기 위해 여러 반복을 실행하는 패턴을 따릅니다. 가능하다면 이러한 핵심 계산을 별도의 함수에 넣는 것이 좋습니다. 예를 들어, 다음의 인위적인 함수는 무작위로 선택된 유형의 배열을 반환합니다:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

이것은 다음과 같이 작성되어야 합니다:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

줄리아의 컴파일러는 함수 경계에서 인수 유형에 맞게 코드를 최적화하므로, 원래 구현에서는 루프 중에 `a`의 유형을 알 수 없습니다(무작위로 선택되기 때문입니다). 따라서 두 번째 버전은 일반적으로 더 빠르며, 내부 루프는 `fill_twos!`의 일환으로 `a`의 다양한 유형에 대해 재컴파일될 수 있습니다.

두 번째 형태는 종종 더 나은 스타일이며 코드 재사용을 더 많이 이끌어낼 수 있습니다.

이 패턴은 Julia Base의 여러 곳에서 사용됩니다. 예를 들어, [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206)의 `vcat` 및 `hcat`을 참조하세요. 또는 우리가 직접 `fill_twos!`를 작성하는 대신 사용할 수 있었던 [`fill!`](@ref) 함수가 있습니다.

`strange_twos`와 같은 함수는 불확실한 유형의 데이터를 다룰 때 발생합니다. 예를 들어, 정수, 부동 소수점, 문자열 또는 다른 무언가를 포함할 수 있는 입력 파일에서 로드된 데이터가 이에 해당합니다.

## [Types with values-as-parameters](@id man-performance-value-type)

`N`-차원 배열을 생성하고 각 축의 크기가 3인 배열을 만들고 싶다고 가정해 보겠습니다. 이러한 배열은 다음과 같이 생성할 수 있습니다:

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

이 접근 방식은 매우 잘 작동합니다: 컴파일러는 `A`가 `Array{Float64,2}`임을 알아낼 수 있습니다. 이는 채우기 값의 타입(`5.0::Float64`)과 차원(`(3, 3)::NTuple{2,Int}`)을 알고 있기 때문입니다. 이는 컴파일러가 같은 함수 내에서 `A`의 향후 사용을 위해 매우 효율적인 코드를 생성할 수 있음을 의미합니다.

하지만 이제 임의의 차원에서 3×3×... 배열을 생성하는 함수를 작성하고 싶다고 가정해 보겠습니다. 함수를 작성하고 싶을 수 있습니다.

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

이것은 작동하지만 (`@code_warntype array3(5.0, 2)`를 사용하여 직접 확인할 수 있습니다) 문제는 출력 유형을 추론할 수 없다는 것입니다: 인수 `N`은 `Int` 유형의 *값*이며, 유형 추론은 그 값을 미리 예측할 수 없습니다. 이는 이 함수의 출력을 사용하는 코드가 보수적이어야 하며, `A`에 대한 각 접근 시 유형을 확인해야 함을 의미합니다. 이러한 코드는 매우 느릴 것입니다.

이제 이러한 문제를 해결하는 매우 좋은 방법 중 하나는 [function-barrier technique](@ref kernel-functions)를 사용하는 것입니다. 그러나 경우에 따라 유형 불안정을 완전히 제거하고 싶을 수 있습니다. 이러한 경우, 한 가지 접근 방식은 차원을 매개변수로 전달하는 것입니다. 예를 들어 `Val{T}()`를 통해 전달할 수 있습니다(참조: ["Value types"](@ref)):

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

줄리아는 두 번째 매개변수로 `Val{::Int}` 인스턴스를 허용하는 특수화된 버전의 `ntuple`을 가지고 있습니다. `N`을 타입 매개변수로 전달함으로써, 이 "값"을 컴파일러에 알려줍니다. 결과적으로, 이 버전의 `array3`는 컴파일러가 반환 타입을 예측할 수 있도록 합니다.

그러나 이러한 기술을 사용하는 것은 놀랍도록 미묘할 수 있습니다. 예를 들어, 다음과 같은 함수에서 `array3`를 호출한다면 도움이 되지 않을 것입니다:

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

여기서, 당신은 다시 같은 문제를 만들어냈습니다: 컴파일러는 `n`이 무엇인지 추측할 수 없으므로 `Val(n)`의 *타입*을 알지 못합니다. `Val`을 사용하려고 하지만 잘못 사용하면 많은 상황에서 성능이 *더 나빠질* 수 있습니다. (효과적으로 `Val`을 함수 장벽 트릭과 결합하여 커널 함수를 더 효율적으로 만들려는 상황에서만 위와 같은 코드가 사용되어야 합니다.)

`Val`의 올바른 사용 예는 다음과 같습니다:

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

이 예제에서 `N`은 매개변수로 전달되므로 그 "값"은 컴파일러에 의해 알려집니다. 본질적으로 `Val(T)`는 `T`가 하드코딩되거나 리터럴(`Val(3)`)이거나 이미 타입 도메인에 지정된 경우에만 작동합니다.

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

한 번 다중 디스패치를 이해하게 되면, 모든 것에 사용하려는 경향이 생기는 것은 이해할 수 있습니다. 예를 들어, 정보를 저장하는 데 사용하고 싶을 수도 있습니다.

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

그리고 나서 `Car{:Honda,:Accord}(year, args...)`와 같은 객체에 대해 디스패치합니다.

다음 중 하나가 참일 때 이것은 가치가 있을 수 있습니다:

  * 각 `Car`에 대해 CPU 집약적인 처리가 필요하며, 컴파일 시간에 `Make`와 `Model`을 알면 훨씬 더 효율적이 됩니다. 사용될 서로 다른 `Make` 또는 `Model`의 총 수가 너무 많지 않을 경우에 해당합니다.
  * 동일한 유형의 `Car` 목록이 있으므로, 이를 모두 `Array{Car{:Honda,:Accord},N}`에 저장할 수 있습니다.

후자가 성립할 때, 이러한 동질 배열을 처리하는 함수는 생산적으로 특화될 수 있습니다: 줄리아는 각 요소의 유형을 미리 알고 있습니다(컨테이너의 모든 객체가 동일한 구체적 유형을 가집니다), 따라서 줄리아는 함수가 컴파일될 때 올바른 메서드 호출을 "조회"할 수 있으며(실행 시간에 확인할 필요가 없음) 전체 목록을 처리하기 위한 효율적인 코드를 생성할 수 있습니다.

이러한 조건이 충족되지 않으면, 이익을 얻지 못할 가능성이 높습니다. 더 나쁘게는, 결과적으로 "유형의 조합 폭발"이 역효과를 낳을 것입니다. 만약 `items[i+1]`가 `item[i]`와 다른 유형을 가지고 있다면, Julia는 런타임에 유형을 조회하고, 메서드 테이블에서 적절한 메서드를 검색하며, (유형 교차를 통해) 어떤 것이 일치하는지 결정하고, 아직 JIT 컴파일이 되었는지 확인한 후 (아직 컴파일되지 않았다면 그렇게 하고), 호출을 수행해야 합니다. 본질적으로, 당신은 전체 유형 시스템과 JIT 컴파일 기계가 기본적으로 당신의 코드에서 switch 문이나 사전 조회를 실행하도록 요청하는 것입니다.

일부 런타임 벤치마크는 (1) 타입 디스패치, (2) 딕셔너리 조회, (3) "스위치" 문을 비교한 내용을 [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ)에서 찾을 수 있습니다.

아마도 실행 시간에 미치는 영향보다 더 나쁜 것은 컴파일 시간에 미치는 영향입니다: Julia는 각기 다른 `Car{Make, Model}`에 대해 특화된 함수를 컴파일합니다; 만약 수백 또는 수천 개의 이러한 유형이 있다면, 그러한 객체를 매개변수로 받아들이는 모든 함수(당신이 직접 작성할 수 있는 사용자 정의 `get_year` 함수부터 Julia Base의 일반 `push!` 함수까지)는 수백 또는 수천 개의 변형이 컴파일될 것입니다. 이러한 각각은 컴파일된 코드의 캐시 크기, 내부 메서드 목록의 길이 등을 증가시킵니다. 값-매개변수에 대한 과도한 열정은 쉽게 막대한 자원을 낭비할 수 있습니다.

## [Access arrays in memory order, along columns](@id man-performance-column-major)

줄리아의 다차원 배열은 열 우선 순서로 저장됩니다. 이는 배열이 한 번에 하나의 열씩 쌓인다는 것을 의미합니다. 이는 아래와 같이 `vec` 함수나 `[:]` 구문을 사용하여 확인할 수 있습니다(배열이 `[1 3 2 4]` 순서로 정렬되어 있고, `[1 2 3 4]`가 아님을 주목하세요):

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

이 배열 정렬 방식은 Fortran, Matlab, R과 같은 많은 언어에서 일반적입니다(몇 가지 예를 들면). 열 우선 정렬의 대안은 행 우선 정렬이며, 이는 C와 Python(`numpy`)을 포함한 다른 언어에서 채택한 규칙입니다. 배열의 정렬 방식을 기억하는 것은 배열을 반복할 때 성능에 상당한 영향을 미칠 수 있습니다. 염두에 두어야 할 경험 법칙은 열 우선 배열의 경우 첫 번째 인덱스가 가장 빠르게 변화한다는 것입니다. 본질적으로 이는 내부 루프 인덱스가 슬라이스 표현식에서 가장 먼저 나타날 경우 반복이 더 빨라질 것임을 의미합니다. `:`로 배열에 인덱싱하는 것은 특정 차원 내의 모든 요소에 반복적으로 접근하는 암시적 루프라는 점을 기억하세요. 예를 들어, 열을 추출하는 것이 행을 추출하는 것보다 더 빠를 수 있습니다.

다음과 같은 인위적인 예를 고려해 보십시오. [`Vector`](@ref)를 받아들이고 입력 벡터의 복사본으로 행 또는 열이 채워진 정사각형 [`Matrix`](@ref)를 반환하는 함수를 작성하고 싶다고 가정해 보겠습니다. 행 또는 열이 이러한 복사본으로 채워지는 것이 중요하지 않다고 가정합니다(아마도 나머지 코드는 그에 따라 쉽게 조정될 수 있습니다). 우리는 최소한 네 가지 방법으로 이를 수행할 수 있을 것입니다(내장된 [`repeat`](@ref)에 대한 권장 호출을 제외하고):

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

이제 동일한 무작위 `10000` x `1` 입력 벡터를 사용하여 각 함수의 실행 시간을 측정하겠습니다:

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

`copy_cols`가 `copy_rows`보다 훨씬 빠르다는 점에 유의하세요. 이는 `copy_cols`가 `Matrix`의 열 기반 메모리 레이아웃을 존중하고 한 번에 하나의 열을 채우기 때문에 예상되는 결과입니다. 또한, `copy_col_row`가 `copy_row_col`보다 훨씬 빠른 이유는 슬라이스 표현식에서 처음 나타나는 요소가 가장 안쪽 루프와 결합되어야 한다는 우리의 경험 법칙을 따르기 때문입니다.

## Pre-allocating outputs

함수가 `Array` 또는 다른 복잡한 유형을 반환하는 경우, 메모리를 할당해야 할 수 있습니다. 불행히도, 종종 할당과 그 반대인 가비지 수집은 상당한 병목 현상이 됩니다.

때때로 각 함수 호출 시 메모리를 할당할 필요를 피하기 위해 출력을 미리 할당할 수 있습니다. 사소한 예로, 비교해 보십시오.

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

with

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

타이밍 결과:

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

사전 할당은 다른 장점이 있습니다. 예를 들어, 호출자가 알고리즘의 "출력" 유형을 제어할 수 있도록 합니다. 위의 예에서, 우리가 원한다면 `SubArray`를 [`Array`](@ref) 대신 전달할 수 있었을 것입니다.

극단적으로 적용하면, 사전 할당이 코드의 가독성을 떨어뜨릴 수 있으므로 성능 측정과 약간의 판단이 필요할 수 있습니다. 그러나 "벡터화된" (요소별) 함수의 경우, 편리한 구문 `x .= f.(y)`를 사용하여 임시 배열 없이 합쳐진 루프와 함께 제자리 작업을 수행할 수 있습니다 (자세한 내용은 [dot syntax for vectorizing functions](@ref man-vectorized)를 참조하십시오).

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

일부 [`Number`](@ref) 하위 유형은 [`BigInt`](@ref) 또는 [`BigFloat`](@ref)와 같이 [`mutable struct`](@ref) 유형으로 구현될 수 있으며, 변경 가능한 구성 요소를 가질 수도 있습니다. Julia `Base`의 산술 인터페이스는 이러한 경우 효율성보다 편리함을 선택하는 경우가 많으므로, 이를 단순하게 사용하는 것은 최적의 성능을 보장하지 않을 수 있습니다. 반면에 [`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics) 패키지의 추상화는 이러한 유형의 변경 가능성을 활용하여 필요한 만큼만 할당하는 빠른 코드를 작성할 수 있게 합니다. `MutableArithmetics`는 또한 필요할 때 변경 가능한 산술 유형의 값을 명시적으로 복사할 수 있게 해줍니다. `MutableArithmetics`는 사용자 패키지이며 Julia 프로젝트와는 관련이 없습니다.

## More dots: Fuse vectorized operations

줄리아는 모든 스칼라 함수를 "벡터화된" 함수 호출로, 모든 연산자를 "벡터화된" 연산자로 변환하는 특별한 [dot syntax](@ref man-vectorized)를 가지고 있으며, 중첩된 "점 호출"이 *융합*되는 특별한 속성을 가지고 있습니다: 이는 구문 수준에서 단일 루프로 결합되어 임시 배열을 할당하지 않습니다. `.=` 및 유사한 할당 연산자를 사용하면 결과를 미리 할당된 배열에 제자리에서 저장할 수도 있습니다 (위 참조).

선형 대수 맥락에서, 이는 `vector + vector` 및 `vector * scalar`와 같은 연산이 정의되어 있더라도, 대신 `vector .+ vector` 및 `vector .* scalar`를 사용하는 것이 유리할 수 있음을 의미합니다. 그 이유는 결과 루프가 주변 계산과 결합될 수 있기 때문입니다. 예를 들어, 두 함수를 고려해 보십시오:

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

두 `f`와 `fdot`는 동일한 작업을 수행합니다. 그러나 `fdot`(매크로 [`@.`](@ref @__dot__)의 도움으로 정의됨)는 배열에 적용할 때 훨씬 더 빠릅니다:

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

즉, `fdot(x)`는 `f(x)`보다 10배 빠르고 메모리를 1/6만큼 할당합니다. 이는 `f(x)`의 각 `*` 및 `+` 연산이 새로운 임시 배열을 할당하고 별도의 루프에서 실행되기 때문입니다. 이 예에서 `f.(x)`는 `fdot(x)`만큼 빠르지만, 많은 상황에서 각 벡터화된 연산에 대해 별도의 함수를 정의하는 것보다 표현식에 점을 추가하는 것이 더 편리합니다.

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

위에서 언급한 점 루프 융합은 고성능 작업을 표현하기 위해 간결하고 관용적인 코드를 가능하게 합니다. 그러나 융합된 작업이 브로드캐스트의 모든 반복에서 계산된다는 점을 기억하는 것이 중요합니다. 이는 특히 구성된 또는 다차원 브로드캐스트가 있는 상황에서 점 호출이 포함된 표현이 의도한 것보다 더 많은 횟수로 함수를 계산할 수 있음을 의미합니다. 예를 들어, 우리는 유클리드 노름이 1인 랜덤 행렬을 만들고 싶다고 가정해 보겠습니다. 우리는 다음과 같은 코드를 작성할 수 있습니다:

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

이것은 작동할 것입니다. 그러나 이 표현식은 실제로 `x[i, :]`의 *모든* 요소에 대해 `sqrt(d[i])`를 다시 계산하므로, 필요 이상으로 많은 제곱근이 계산됩니다. 브로드캐스트가 어떤 인덱스를 반복하는지 정확히 보려면, 융합된 표현식의 인수에 대해 `Broadcast.combine_axes`를 호출할 수 있습니다. 이것은 반복 축에 해당하는 항목을 가진 범위의 튜플을 반환합니다; 이러한 범위의 길이의 곱은 융합된 작업에 대한 총 호출 수가 됩니다.

따라서 방송 표현의 일부 구성 요소가 축을 따라 일정할 때—앞서의 예에서 두 번째 차원에 있는 `sqrt`와 같이—그러한 구성 요소를 강제로 "분리"함으로써 성능 향상의 가능성이 있습니다. 즉, 방송된 연산의 결과를 미리 할당하고 일정한 축을 따라 캐시된 값을 재사용하는 것입니다. 이러한 잠재적인 접근 방식 중 일부는 임시 변수를 사용하거나, 점 표현식의 구성 요소를 `identity`로 감싸거나, 동등한 본질적으로 벡터화된(하지만 비융합된) 함수를 사용하는 것입니다.

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

이러한 옵션 중 어느 것이든 할당의 대가로 약 3배의 속도 향상을 제공합니다. 큰 브로드캐스트 가능한 경우 이 속도 향상은 점근적으로 매우 클 수 있습니다.

## [Consider using views for slices](@id man-performance-views)

줄리아에서 배열 "슬라이스" 표현식인 `array[1:5, :]`는 해당 데이터의 복사본을 생성합니다(할당의 왼쪽에 있는 경우를 제외하고, 여기서 `array[1:5, :] = ...`는 `array`의 해당 부분에 제자리에서 할당합니다). 슬라이스에서 많은 작업을 수행하는 경우, 더 작은 연속 복사본으로 작업하는 것이 원래 배열에 인덱싱하는 것보다 더 효율적이기 때문에 성능에 좋을 수 있습니다. 반면에 슬라이스에서 몇 가지 간단한 작업만 수행하는 경우, 할당 및 복사 작업의 비용이 상당할 수 있습니다.

배열의 "뷰"를 생성하는 대안이 있습니다. 이는 원래 배열의 데이터를 복사하지 않고 제자리에서 참조하는 배열 객체(`SubArray`)입니다. (뷰에 쓰면 원래 배열의 데이터도 수정됩니다.) 이는 [`view`](@ref)를 호출하여 개별 슬라이스에 대해 수행할 수 있으며, 전체 표현식이나 코드 블록에 대해서는 해당 표현식 앞에 [`@views`](@ref)를 넣어 더 간단하게 수행할 수 있습니다. 예를 들어:

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

`fview` 버전의 함수에서 3배 속도 향상과 메모리 할당 감소를 모두 주목하세요.

## Copying data is not always bad

배열은 메모리에 연속적으로 저장되어 CPU 벡터화에 적합하고 캐싱으로 인해 메모리 접근이 줄어듭니다. 이러한 이유로 배열에 열 우선 순서로 접근하는 것이 권장됩니다(위 참조). 불규칙한 접근 패턴과 비연속적인 뷰는 비순차적인 메모리 접근으로 인해 배열의 계산 속도를 크게 저하시킬 수 있습니다.

불규칙하게 접근되는 데이터를 반복적으로 접근하기 전에 연속 배열로 복사하면 큰 속도 향상을 가져올 수 있습니다. 아래 예시와 같이, 행렬이 무작위로 섞인 인덱스에서 접근된 후 곱해집니다. 일반 배열로 복사하면 복사 및 할당의 추가 비용에도 불구하고 곱셈 속도가 빨라집니다.

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

메모리가 충분하다면, 뷰를 배열로 복사하는 비용은 연속 배열에서 반복적인 행렬 곱셈을 수행함으로써 얻는 속도 향상에 비해 상대적으로 적습니다.

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

만약 귀하의 애플리케이션이 고정 크기의 작은 배열(`100 미만` 요소)을 많이 포함하고 있다면(즉, 실행 전에 크기가 알려져 있음), [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl) 사용을 고려해 볼 수 있습니다. 이 패키지는 불필요한 힙 할당을 피하고 컴파일러가 배열의 *크기*에 맞게 코드를 특수화할 수 있도록 배열을 표현할 수 있게 해줍니다. 예를 들어, 벡터 연산을 완전히 펼치고(루프를 제거) CPU 레지스터에 요소를 저장하는 방식입니다.

예를 들어, 2차원 기하학을 사용하여 계산을 수행하는 경우, 2개 구성 요소를 가진 벡터로 많은 계산을 수행할 수 있습니다. StaticArrays.jl의 `SVector` 유형을 사용하면 벡터 `v`와 `w`에 대해 `norm(3v - w)`와 같은 편리한 벡터 표기법과 연산을 사용할 수 있으며, 컴파일러가 코드를 최소한의 계산으로 펼칠 수 있도록 허용합니다. 이는 `@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])`와 동등합니다.

## Avoid string interpolation for I/O

파일(또는 기타 I/O 장치)에 데이터를 쓸 때, 추가적인 중간 문자열을 형성하는 것은 오버헤드의 원인이 됩니다. 대신:

```julia
println(file, "$a $b")
```

사용:

```julia
println(file, a, " ", b)
```

코드의 첫 번째 버전은 문자열을 형성한 다음 파일에 작성하고, 두 번째 버전은 값을 직접 파일에 씁니다. 또한 일부 경우 문자열 보간이 읽기 어려울 수 있음을 유의하세요. 다음을 고려해 보세요:

```julia
println(file, "$(f(a))$(f(b))")
```

대결:

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

원격 함수를 병렬로 실행할 때:

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

보다 빠릅니다:

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

이전 결과는 모든 작업자에게 단일 네트워크 왕복을 발생시키는 반면, 후자는 두 번의 네트워크 호출을 발생시킵니다. 첫 번째는 [`@spawnat`](@ref)에 의해, 두 번째는 [`fetch`](@ref)(또는 심지어 [`wait`](@ref))에 의해 발생합니다. `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566`는 직렬로 실행되고 있어 전반적으로 성능이 저하되고 있습니다.

## Fix deprecation warnings

더 이상 사용되지 않는 함수는 내부적으로 관련 경고를 한 번만 출력하기 위해 조회를 수행합니다. 이 추가 조회는 상당한 속도 저하를 초래할 수 있으므로, 더 이상 사용되지 않는 함수의 모든 사용은 경고에서 제안한 대로 수정되어야 합니다.

## Tweaks

이것들은 긴밀한 내부 루프에서 도움이 될 수 있는 몇 가지 사소한 사항입니다.

  * 불필요한 배열을 피하세요. 예를 들어, [`sum([x,y,z])`](@ref) 대신 `x+y+z`를 사용하세요.
  * Use [`abs2(z)`](@ref) instead of [`abs(z)^2`](@ref) for complex `z`. In general, try to rewrite code to use [`abs2`](@ref) instead of [`abs`](@ref) for complex arguments.
  * Use [`div(x,y)`](@ref) for truncating division of integers instead of [`trunc(x/y)`](@ref), [`fld(x,y)`](@ref) instead of [`floor(x/y)`](@ref), and [`cld(x,y)`](@ref) instead of [`ceil(x/y)`](@ref).

## [Performance Annotations](@id man-performance-annotations)

때때로 특정 프로그램 속성을 약속함으로써 더 나은 최적화를 활성화할 수 있습니다.

  * [`@inbounds`](@ref)를 사용하여 표현식 내에서 배열 경계 검사를 제거하십시오. 이를 수행하기 전에 확실히 확인하십시오. 만약 하위 스크립트가 경계를 벗어나면 충돌이나 무음 손상이 발생할 수 있습니다.
  * [`@fastmath`](@ref)를 사용하여 실수에 대해 올바른 부동 소수점 최적화를 허용하되, IEEE 숫자에 대해 차이를 초래할 수 있습니다. 이를 수행할 때는 주의해야 하며, 이는 수치 결과를 변경할 수 있습니다. 이는 clang의 `-ffast-math` 옵션에 해당합니다.
  * [`@simd`](@ref) 앞에 `for` 루프를 작성하여 반복이 독립적이며 재정렬될 수 있음을 보장합니다. 많은 경우, Julia는 `@simd` 매크로 없이도 코드를 자동으로 벡터화할 수 있습니다. 이는 그러한 변환이 불법이 될 경우에만 유익하며, 여기에는 부동 소수점 재결합을 허용하고 의존 메모리 접근을 무시하는 경우(`@simd ivdep`)가 포함됩니다. 의존 반복이 있는 루프에 `@simd`를 잘못 주석 처리하면 예기치 않은 결과가 발생할 수 있으므로 주의해야 합니다. 특히, 일부 `AbstractArray` 하위 유형에서 `setindex!`는 반복 순서에 본질적으로 의존한다는 점에 유의하십시오. **이 기능은 실험적이며** 향후 Julia 버전에서 변경되거나 사라질 수 있습니다.

1:n을 사용하여 AbstractArray에 인덱싱하는 일반적인 관용구는 배열이 비정상적인 인덱싱을 사용하는 경우 안전하지 않으며, 경계 검사가 꺼져 있으면 세그멘테이션 오류를 일으킬 수 있습니다. 대신 `LinearIndices(x)` 또는 `eachindex(x)`를 사용하세요 (또한 [Arrays with custom indices](@ref man-custom-indices)를 참조하세요).

!!! note
    `@simd`는 가장 안쪽 `for` 루프 바로 앞에 배치해야 하지만, `@inbounds`와 `@fastmath`는 단일 표현식이나 중첩된 코드 블록 내에 나타나는 모든 표현식에 적용할 수 있습니다. 예를 들어, `@inbounds begin` 또는 `@inbounds for ...`를 사용할 수 있습니다.


여기 `@inbounds`와 `@simd` 마크업이 모두 포함된 예가 있습니다 (우리는 여기서 최적화 프로그램이 너무 똑똑해져서 우리의 벤치마크를 무너뜨리지 않도록 `@noinline`을 사용합니다):

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

2.4GHz 인텔 코어 i5 프로세서가 장착된 컴퓨터에서, 이는 다음을 생성합니다:

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sec`는 성능을 측정하며, 숫자가 클수록 더 좋습니다.)

여기 세 가지 종류의 마크업이 모두 포함된 예가 있습니다. 이 프로그램은 먼저 일차원 배열의 유한 차분을 계산한 다음, 결과의 L2-노름을 평가합니다:

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

2.7 GHz 인텔 코어 i7 프로세서가 장착된 컴퓨터에서, 이는 다음을 생성합니다:

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

여기서 옵션 `--math-mode=ieee`는 `@fastmath` 매크로를 비활성화하여 결과를 비교할 수 있도록 합니다.

이 경우 `@fastmath`로 인한 속도 향상은 약 3.7배입니다. 이는 비정상적으로 큰 수치로, 일반적으로 속도 향상은 더 작습니다. (이 특정 예제에서 벤치마크의 작업 세트는 프로세서의 L1 캐시에 들어갈 만큼 작기 때문에 메모리 접근 지연이 영향을 미치지 않으며, 계산 시간은 CPU 사용에 의해 지배됩니다. 많은 실제 프로그램에서는 이러한 경우가 아닙니다.) 또한, 이 경우 이 최적화는 결과를 변경하지 않습니다. 일반적으로 결과는 약간 다를 것입니다. 어떤 경우에는, 특히 수치적으로 불안정한 알고리즘의 경우 결과가 매우 다를 수 있습니다.

주석 `@fastmath`는 부동 소수점 표현식을 재배치합니다. 예를 들어, 평가 순서를 변경하거나 특정 특수 사례(무한대, NaN)가 발생하지 않는다고 가정합니다. 이 경우(그리고 이 특정 컴퓨터에서), 주요 차이점은 함수 `deriv`에서 표현식 `1 / (2*dx)`가 루프 밖으로 끌어올려진다는 것입니다(즉, 루프 외부에서 계산됨). 마치 `idx = 1 / (2*dx)`라고 작성한 것처럼 됩니다. 루프 내에서 표현식 `... / (2*dx)`는 `... * idx`로 바뀌며, 이는 훨씬 더 빠르게 평가됩니다. 물론, 컴파일러가 적용하는 실제 최적화와 결과적인 속도 향상은 하드웨어에 매우 의존적입니다. 생성된 코드의 변화를 확인하려면 Julia의 [`code_native`](@ref) 함수를 사용할 수 있습니다.

`@fastmath`는 계산 중에 `NaN`이 발생하지 않을 것이라고 가정하므로, 이는 놀라운 동작을 초래할 수 있습니다:

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

서브노멀 숫자, 이전에 [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number)라고 불렸던 이 숫자는 많은 맥락에서 유용하지만 일부 하드웨어에서는 성능 저하를 초래합니다. 호출 [`set_zero_subnormals(true)`](@ref)는 부동 소수점 연산이 서브노멀 입력 또는 출력을 제로로 처리하도록 허용하여 일부 하드웨어에서 성능을 향상시킬 수 있습니다. 호출 [`set_zero_subnormals(false)`](@ref)는 서브노멀 숫자에 대해 엄격한 IEEE 동작을 강제합니다.

아래는 서브노말이 일부 하드웨어에서 성능에 눈에 띄게 영향을 미치는 예입니다:

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

이것은 다음과 유사한 출력을 제공합니다.

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

각 짝수 반복이 훨씬 더 빠르다는 점에 유의하세요.

이 예제는 `a`의 값이 지수적으로 감소하는 곡선을 생성하여 시간이 지남에 따라 서서히 평평해지기 때문에 많은 비정상 숫자를 생성합니다.

서브노말을 0으로 취급하는 것은 주의해서 사용해야 합니다. 그렇게 하면 `x-y == 0`이 `x == y`를 의미하는 일부 항등식이 깨지기 때문입니다:

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

일부 응용 프로그램에서는 비정상 숫자를 0으로 설정하는 대신 미세한 노이즈를 주입하는 대안이 있습니다. 예를 들어, `a`를 0으로 초기화하는 대신 다음과 같이 초기화합니다:

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

매크로 [`@code_warntype`](@ref) (또는 그 함수 변형 [`code_warntype`](@ref))는 때때로 타입 관련 문제를 진단하는 데 유용할 수 있습니다. 다음은 예시입니다:

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

Interpreting the output of [`@code_warntype`](@ref), like that of its cousins [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_llvm`](@ref), and [`@code_native`](@ref), takes a little practice. Your code is being presented in form that has been heavily digested on its way to generating compiled machine code. Most of the expressions are annotated by a type, indicated by the `::T` (where `T` might be [`Float64`](@ref), for example). The most important characteristic of [`@code_warntype`](@ref) is that non-concrete types are displayed in red; since this document is written in Markdown, which has no color, in this document, red text is denoted by uppercase.

함수의 추론된 반환 유형은 `Body::Float64`로 표시됩니다. 다음 줄은 Julia의 SSA IR 형식으로 `f`의 본체를 나타냅니다. 번호가 매겨진 상자는 레이블이며 코드에서 점프(즉, `goto`)의 대상을 나타냅니다. 본체를 살펴보면, 가장 먼저 `pos`가 호출되고 반환 값은 대문자로 표시된 비구체적 유형인 `Union` 유형 `Union{Float64, Int64}`로 추론됩니다. 이는 입력 유형에 따라 `pos`의 정확한 반환 유형을 알 수 없음을 의미합니다. 그러나 `y*x`의 결과는 `y`가 `Float64`이든 `Int64`이든 관계없이 `Float64`입니다. 따라서 `f(x::Float64)`는 일부 중간 계산이 유형 불안정하더라도 출력에서 유형 불안정하지 않습니다.

이 정보를 어떻게 사용할지는 당신에게 달려 있습니다. 분명히, `pos`를 타입 안정적으로 고정하는 것이 가장 좋습니다: 그렇게 하면 `f`의 모든 변수는 구체적이 되고 성능이 최적화됩니다. 그러나 이러한 *일시적인* 타입 불안정성이 그리 중요하지 않을 수 있는 상황도 있습니다: 예를 들어, `pos`가 독립적으로 사용되지 않는 경우, `f`의 출력이 타입 안정적이라는 사실(입력 [`Float64`](@ref)에 대해)은 이후 코드가 타입 불안정성의 전파 효과로부터 보호받게 합니다. 이는 타입 불안정성을 수정하기 어려운 경우에 특히 관련이 있습니다. 이러한 경우, 위의 팁(예: 타입 주석 추가 및/또는 함수 분할)은 타입 불안정성으로 인한 "피해"를 제한하는 데 가장 좋은 도구입니다. 또한, Julia Base조차도 타입 불안정한 함수가 있다는 점에 유의하세요. 예를 들어, 함수 [`findfirst`](@ref)는 키가 발견된 배열의 인덱스를 반환하거나, 발견되지 않으면 `nothing`을 반환하는 명확한 타입 불안정성을 가지고 있습니다. 중요한 타입 불안정성을 찾기 쉽게 하기 위해, `missing` 또는 `nothing`을 포함하는 `Union`은 빨간색 대신 노란색으로 강조 표시됩니다.

다음 예제는 비단말 유형이 포함된 것으로 표시된 표현식을 해석하는 데 도움이 될 수 있습니다:

  * `Body::Union{T1,T2})`로 시작하는 함수 본문

      * 해석: 불안정한 반환 유형을 가진 함수
      * 제안: 반환 값의 유형 안정성을 유지하되, 주석을 추가해야 할 경우에도 그렇게 하세요.
  * `invoke Main.g(%%x::Int64)::Union{Float64, Int64}`

      * 해석: 타입이 불안정한 함수 `g`에 대한 호출.
      * 제안: 함수를 수정하거나 필요하다면 반환 값을 주석 처리하세요.
  * `invoke Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * 해석: 잘못된 타입의 배열 요소 접근
      * 제안: 더 잘 정의된 타입의 배열을 사용하거나, 필요하다면 개별 요소 접근의 타입을 주석으로 달아주세요.
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} where N`

      * 해석: 비리프 타입의 필드를 가져오는 것. 이 경우, `x`의 타입인 `ArrayContainer`는 `data::Array{T}`라는 필드를 가지고 있다. 그러나 `Array`는 구체적인 타입이 되기 위해서 차원 `N`도 필요하다.
      * 제안: `Array{T,3}` 또는 `Array{T,N}`와 같은 구체적인 타입을 사용하세요. 여기서 `N`은 이제 `ArrayContainer`의 매개변수입니다.

## [Performance of captured variable](@id man-performance-captured)

다음은 내부 함수를 정의하는 예제입니다:

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

함수 `abmult`는 인수를 `r`의 절대값으로 곱하는 함수 `f`를 반환합니다. `f`에 할당된 내부 함수는 "클로저"라고 불립니다. 내부 함수는 `do` 블록과 생성기 표현식에 대해서도 언어에 의해 사용됩니다.

이 코드 스타일은 언어에 성능 문제를 일으킵니다. 파서는 이를 저수준 명령어로 변환할 때 위의 코드를 상당히 재구성하여 내부 함수를 별도의 코드 블록으로 추출합니다. 내부 함수와 그 외부 범위에서 공유되는 "캡처된" 변수인 `r`과 같은 변수도 내부 및 외부 함수 모두에서 접근할 수 있는 힙 할당 "상자"로 추출됩니다. 이는 언어가 내부 범위의 `r`이 외부 범위의 `r`과 동일해야 하며, 외부 범위(또는 다른 내부 함수)가 `r`을 수정한 후에도 동일해야 한다고 명시하기 때문입니다.

앞서 언급한 단락에서는 "파서"에 대해 언급했습니다. 즉, `abmult`가 포함된 모듈이 처음 로드될 때 발생하는 컴파일 단계로, 처음 호출될 때의 후속 단계와는 다릅니다. 파서는 `Int`가 고정된 타입이라는 것을 "모르며", `r = -r`이라는 문장이 `Int`를 다른 `Int`로 변환한다는 것도 알지 못합니다. 타입 추론의 마법은 컴파일의 후속 단계에서 발생합니다.

따라서 파서는 `r`이 고정된 타입(`Int`)을 가지고 있지 않다는 것과 내부 함수가 생성된 후 `r`의 값이 변경되지 않는다는 것을 알지 못합니다(따라서 박스가 필요하지 않습니다). 따라서 파서는 `Any`와 같은 추상 타입을 가진 객체를 담고 있는 박스에 대한 코드를 생성합니다. 이는 `r`이 발생할 때마다 런타임 타입 디스패치를 요구합니다. 이는 위의 함수에 `@code_warntype`를 적용하여 확인할 수 있습니다. 박싱과 런타임 타입 디스패치는 성능 손실을 초래할 수 있습니다.

성능이 중요한 코드 섹션에서 캡처된 변수가 사용되는 경우, 다음 팁은 그 사용이 성능적으로 효율적이도록 도와줍니다. 첫째, 캡처된 변수가 타입이 변경되지 않는 것이 알려져 있다면, 이는 타입 주석을 사용하여 명시적으로 선언할 수 있습니다(변수에 대해, 오른쪽에는 적용하지 않음):

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

타입 주석은 파서가 박스 안의 객체에 구체적인 타입을 연관시킬 수 있기 때문에 캡처로 인해 손실된 성능을 부분적으로 회복합니다. 더 나아가, 캡처된 변수가 전혀 박스화될 필요가 없을 경우(클로저가 생성된 후 재할당되지 않기 때문에), 다음과 같이 `let` 블록으로 이를 표시할 수 있습니다.

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

`let` 블록은 범위가 내부 함수에만 국한된 새로운 변수 `r`을 생성합니다. 두 번째 기법은 캡처된 변수가 있는 경우 전체 언어 성능을 회복합니다. 이는 컴파일러의 빠르게 진화하는 측면이며, 향후 릴리스에서는 성능을 달성하기 위해 이러한 정도의 프로그래머 주석이 필요하지 않을 가능성이 높습니다. 그동안 `abmult3`와 같이 `let` 문 삽입을 자동화하는 일부 사용자 기여 패키지인 [FastClosures](https://github.com/c42f/FastClosures.jl)가 있습니다.

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

이 섹션은 각 스레드에서 선형 대수 연산을 수행하는 다중 스레드 Julia 코드에 적용됩니다. 실제로 이러한 선형 대수 연산은 BLAS / LAPACK 호출을 포함하며, 이 호출 자체도 다중 스레드입니다. 이 경우, 두 가지 유형의 다중 스레드로 인해 코어가 과도하게 사용되지 않도록 해야 합니다.

줄리아는 선형 대수를 위해 OpenBLAS의 자체 복사본을 컴파일하고 사용하며, 스레드 수는 환경 변수 `OPENBLAS_NUM_THREADS`에 의해 제어됩니다. 이는 줄리아를 시작할 때 명령줄 옵션으로 설정하거나, 줄리아 세션 중에 `BLAS.set_num_threads(N)`를 사용하여 수정할 수 있습니다(서브모듈 `BLAS`는 `using LinearAlgebra`에 의해 내보내집니다). 현재 값은 `BLAS.get_num_threads()`로 접근할 수 있습니다.

사용자가 아무것도 지정하지 않으면, Julia는 OpenBLAS 스레드 수에 대해 합리적인 값을 선택하려고 합니다(예: 플랫폼, Julia 버전 등을 기반으로). 그러나 일반적으로 값을 수동으로 확인하고 설정하는 것이 권장됩니다. OpenBLAS의 동작은 다음과 같습니다:

  * `OPENBLAS_NUM_THREADS=1`인 경우, OpenBLAS는 호출하는 Julia 스레드(s)를 사용합니다. 즉, 계산을 실행하는 Julia 스레드에서 "작동"합니다.
  * `OPENBLAS_NUM_THREADS=N>1`인 경우, OpenBLAS는 자체적으로 `N`개의 스레드 풀을 생성하고 관리합니다. 모든 Julia 스레드 간에 공유되는 단 하나의 OpenBLAS 스레드 풀이 있습니다.

Julia를 다중 스레드 모드로 시작할 때 `JULIA_NUM_THREADS=X`를 사용하면 일반적으로 `OPENBLAS_NUM_THREADS=1`로 설정하는 것이 권장됩니다. 위에서 설명한 동작을 고려할 때, BLAS 스레드 수를 `N>1`로 늘리면 성능이 저하될 수 있으며, 특히 `N<<X`인 경우에 더욱 그렇습니다. 그러나 이는 단지 경험 법칙일 뿐이며, 각 스레드 수를 설정하는 가장 좋은 방법은 특정 애플리케이션에서 실험해 보는 것입니다.

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

OpenBLAS의 대안으로, 선형 대수 성능을 향상시킬 수 있는 여러 다른 백엔드가 존재합니다. 주요 예로는 [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl)와 [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl)가 있습니다.

이들은 외부 패키지이므로 여기서 자세히 논의하지 않겠습니다. 각 패키지의 문서를 참조하시기 바랍니다(특히 멀티스레딩과 관련하여 OpenBLAS와 다른 동작을 보이기 때문입니다).

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

처음으로 줄리아 메서드가 호출되면, 그것과 호출하는 모든 메서드(또는 정적으로 결정할 수 있는 메서드)는 컴파일됩니다. [`@time`](@ref) 매크로 패밀리가 이를 보여줍니다.

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

`@time @eval`는 컴파일 시간을 측정하는 데 더 좋습니다. 왜냐하면 [`@eval`](@ref) 없이 일부 컴파일이 타이밍이 시작되기 전에 이미 완료될 수 있기 때문입니다.

패키지를 개발할 때, 사용자가 패키지를 사용할 때 이미 컴파일된 코드를 사용할 수 있도록 *사전 컴파일*을 통해 사용자 경험을 개선할 수 있습니다. 패키지 코드를 효과적으로 사전 컴파일하려면, [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/)를 사용하여 사전 컴파일 시간 동안 일반적인 패키지 사용을 대표하는 "사전 컴파일 작업 부하"를 실행하는 것이 좋습니다. 이렇게 하면 네이티브 컴파일된 코드가 패키지 `pkgimage` 캐시에 캐시되어, 이러한 사용에 대한 "첫 실행 시간" (종종 TTFX라고 함)을 크게 줄일 수 있습니다.

[`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) 작업 부하는 비활성화할 수 있으며, 패키지 개발 중에 추가적인 시간 소모를 원하지 않는 경우 환경 설정을 통해 구성할 수 있습니다.

### Reducing package loading time

패키지 로드 시간을 줄이는 것은 일반적으로 유용합니다. 패키지 개발자를 위한 일반적인 모범 사례는 다음과 같습니다:

1. 필요한 의존성만 유지하세요. 필수 의존성을 부풀리지 않고 다른 패키지와의 상호 운용성을 지원하기 위해 [package extensions](@ref) 사용을 고려하세요.
2. [`__init__()`](@ref) 함수를 대체할 방법이 없을 경우를 제외하고는 사용을 피하십시오. 특히 많은 컴파일을 유발하거나 실행하는 데 오랜 시간이 걸릴 수 있는 함수는 더욱 그렇습니다.
3. 가능한 경우, 종속성 및 패키지 코드에서 [invalidations](https://julialang.org/blog/2020/08/invalidations/)를 수정하십시오.

도구 [`@time_imports`](@ref)는 REPL에서 위의 요소를 검토하는 데 유용할 수 있습니다.

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

이 예제에서는 여러 패키지가 로드되며, 그 중 일부는 `__init__()` 함수를 가지고 있고, 일부는 컴파일을 유발하며, 그 중 일부는 재컴파일을 유발합니다. 재컴파일은 이전 패키지가 메서드를 무효화하여 발생하며, 이러한 경우 다음 패키지가 `__init__()` 함수를 실행할 때 코드가 실행되기 전에 재컴파일이 발생하는 경우가 있습니다.

또한, `SparseArrays`가 의존성 트리에 있기 때문에 `Statistics` 확장 `SparseArraysExt`가 활성화되었음을 주의하세요. 즉, `0.4 ms  Statistics → SparseArraysExt`를 참조하세요.

이 보고서는 의존성 로드 시간의 비용이 제공하는 기능에 비해 가치가 있는지 검토할 좋은 기회를 제공합니다. 또한 `Pkg` 유틸리티의 `why`를 사용하여 간접 의존성이 존재하는 이유를 보고할 수 있습니다.

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

패키지가 가져오는 간접 의존성을 보려면, `pkg> rm` 명령어로 패키지를 제거하고, 매니페스트에서 제거된 의존성을 확인한 다음, `pkg> undo` 명령어로 변경 사항을 되돌릴 수 있습니다.

로딩 시간이 느린 `__init__()` 메서드의 컴파일에 의해 지배되는 경우, 어떤 것이 컴파일되고 있는지를 식별하는 한 가지 장황한 방법은 줄리아 인수 `--trace-compile=stderr`를 사용하는 것입니다. 이 인수는 메서드가 컴파일될 때마다 [`precompile`](@ref) 문장을 보고합니다. 예를 들어, 전체 설정은 다음과 같습니다:

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

`--startup-file=no`는 `startup.jl`에 있을 수 있는 패키지로부터 테스트를 격리하는 데 도움이 됩니다.

재컴파일 이유에 대한 더 많은 분석은 [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl) 패키지를 통해 달성할 수 있습니다.
