```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia는 빠른 개발이 진행 중이며 여러 플랫폼에서 기능을 검증하기 위한 광범위한 테스트 스위트를 갖추고 있습니다. 소스에서 Julia를 빌드하면 `make test`를 사용하여 이 테스트 스위트를 실행할 수 있습니다. 바이너리 설치에서는 `Base.runtests()`를 사용하여 테스트 스위트를 실행할 수 있습니다.

```@docs
Base.runtests
```

## Basic Unit Tests

`Test` 모듈은 간단한 *단위 테스트* 기능을 제공합니다. 단위 테스트는 결과가 예상한 대로인지 확인하여 코드가 올바른지 확인하는 방법입니다. 변경 후에도 코드가 여전히 작동하는지 확인하는 데 유용하며, 개발 중에 코드가 완성되었을 때 가져야 할 동작을 지정하는 방법으로 사용할 수 있습니다. 또한 [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package)에 대한 문서도 확인해 보시기 바랍니다.

간단한 단위 테스트는 `@test` 및 `@test_throws` 매크로를 사용하여 수행할 수 있습니다:

```@docs
Test.@test
Test.@test_throws
```

예를 들어, 새로운 함수 `foo(x)`가 예상대로 작동하는지 확인하고 싶다고 가정해 보겠습니다:

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

조건이 참이면 `Pass`가 반환됩니다:

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

조건이 거짓이면 `Fail`이 반환되고 예외가 발생합니다:

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

조건을 평가할 수 없었던 경우, 이 경우 `length`가 기호에 대해 정의되지 않았기 때문에 예외가 발생하면 `Error` 객체가 반환되고 예외가 발생합니다:

```julia-repl
julia> @test foo(:cat) == 1
Error During Test
  Test threw an exception of type MethodError
  Expression: foo(:cat) == 1
  MethodError: no method matching length(::Symbol)
  The function `length` exists, but no method is defined for this combination of argument types.

  Closest candidates are:
    length(::SimpleVector) at essentials.jl:256
    length(::Base.MethodList) at reflection.jl:521
    length(::MethodTable) at reflection.jl:597
    ...
  Stacktrace:
  [...]
ERROR: There was an error during testing
```

우리가 표현식을 평가할 때 *예상대로* 예외가 발생해야 한다고 생각한다면, `@test_throws`를 사용하여 이것이 발생하는지 확인할 수 있습니다:

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

일반적으로 많은 수의 테스트가 사용되어 함수가 다양한 입력에 대해 올바르게 작동하는지 확인합니다. 테스트가 실패할 경우 기본 동작은 즉시 예외를 발생시키는 것입니다. 그러나 일반적으로는 나머지 테스트를 먼저 실행하여 테스트 중인 코드에서 얼마나 많은 오류가 있는지 더 잘 파악하는 것이 바람직합니다.

!!! note
    `@testset`는 그 안에서 테스트를 실행할 때 자체적인 로컬 범위를 생성합니다.


`@testset` 매크로는 테스트를 *세트*로 그룹화하는 데 사용할 수 있습니다. 테스트 세트의 모든 테스트가 실행되며, 테스트 세트가 끝나면 요약이 출력됩니다. 테스트 중 하나라도 실패하거나 오류로 인해 평가할 수 없는 경우, 테스트 세트는 `TestSetException`을 발생시킵니다.

```@docs
Test.@testset
Test.TestSetException
```

우리는 `foo(x)` 함수에 대한 테스트를 테스트 세트에 넣을 수 있습니다:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

테스트 세트는 중첩될 수도 있습니다:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
```

함수 호출 외에도:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

이것은 테스트 세트의 인수 분해를 허용하는 데 사용될 수 있으며, 관련 함수를 대신 실행하여 개별 테스트 세트를 실행하는 것이 더 쉬워집니다. 함수의 경우, 테스트 세트는 호출된 함수의 이름이 부여됩니다. 중첩된 테스트 세트에 실패가 없는 경우, 여기서 발생한 것처럼 요약에서 숨겨지며, `verbose=true` 옵션이 전달되지 않는 한 그렇습니다:

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset verbose = true "Foo Tests" begin
           @testset "Animals" begin
               @test foo("cat") == 9
               @test foo("dog") == foo("cat")
           end
           @testset "Arrays $i" for i in 1:3
               @test foo(zeros(i)) == i^2
               @test foo(fill(1.0, i)) == i^2
           end
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    8      8  0.0s
  Animals     |    2      2  0.0s
  Arrays 1    |    2      2  0.0s
  Arrays 2    |    2      2  0.0s
  Arrays 3    |    2      2  0.0s
```

테스트 실패가 발생할 경우, 실패한 테스트 세트에 대한 세부 정보만 표시됩니다:

```julia-repl; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @testset "Animals" begin
               @testset "Felines" begin
                   @test foo("cat") == 9
               end
               @testset "Canines" begin
                   @test foo("dog") == 9
               end
           end
           @testset "Arrays" begin
               @test foo(zeros(2)) == 4
               @test foo(fill(1.0, 4)) == 15
           end
       end

Arrays: Test Failed
  Expression: foo(fill(1.0, 4)) == 15
   Evaluated: 16 == 15
[...]
Test Summary: | Pass  Fail  Total  Time
Foo Tests     |    3     1      4  0.0s
  Animals     |    2            2  0.0s
  Arrays      |    1     1      2  0.0s
ERROR: Some tests did not pass: 3 passed, 1 failed, 0 errored, 0 broken.
```

## Testing Log Statements

[`@test_logs`](@ref) 매크로를 사용하여 로그 문을 테스트하거나 [`TestLogger`](@ref)를 사용할 수 있습니다.

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

부동 소수점 값에 대한 계산이 부정확할 수 있으므로, `@test a ≈ b`를 사용하여 근사 동등성 검사를 수행할 수 있습니다(여기서 `≈`, `\approx`의 탭 완성을 통해 입력됨, [`isapprox`](@ref) 함수임) 또는 `4d61726b646f776e2e436f64652822222c20226973617070726f782229_40726566`를 직접 사용할 수 있습니다.

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

상대 및 절대 허용 오차는 `≈` 비교 후 `isapprox`의 `rtol` 및 `atol` 키워드 인수를 설정하여 지정할 수 있습니다:

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

`≈`의 특정 기능이 아니라 `@test` 매크로의 일반적인 기능임을 유의하십시오: `@test a <op> b key=val`은 매크로에 의해 `@test op(a, b, key=val)`로 변환됩니다. 그러나 이는 `≈` 테스트에 특히 유용합니다.

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

테스트가 지속적으로 실패하면 `@test_broken` 매크로를 사용하도록 변경할 수 있습니다. 이렇게 하면 테스트가 계속 실패할 경우 `Broken`으로 표시되며, 테스트가 성공할 경우 사용자에게 `Error`로 알림을 보냅니다.

```@docs
Test.@test_broken
```

`@test_skip`는 평가 없이 테스트를 건너뛰는 데에도 사용할 수 있지만, 테스트 세트 보고서에서 건너뛴 테스트를 포함합니다. 테스트는 실행되지 않지만 `Broken` `Result`를 제공합니다.

```@docs
Test.@test_skip
```

## Test result types

```@docs
Test.Result
Test.Pass
Test.Fail
Test.Error
Test.Broken
```

## Creating Custom `AbstractTestSet` Types

패키지는 `record` 및 `finish` 메서드를 구현하여 자체 `AbstractTestSet` 하위 유형을 생성할 수 있습니다. 하위 유형은 설명 문자열을 인수로 받는 단일 인수 생성자를 가져야 하며, 모든 옵션은 키워드 인수로 전달되어야 합니다.

```@docs
Test.record
Test.finish
```

`Test`는 실행되는 동안 중첩된 테스트 세트의 스택을 유지하는 책임을 지지만, 결과 누적은 `AbstractTestSet` 하위 유형의 책임입니다. 이 스택은 `get_testset` 및 `get_testset_depth` 메서드를 사용하여 접근할 수 있습니다. 이러한 함수는 내보내지 않음을 유의하십시오.

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test`는 또한 중첩된 `@testset` 호출이 부모와 동일한 `AbstractTestSet` 하위 유형을 사용하도록 보장합니다. 명시적으로 설정하지 않는 한 그렇습니다. 테스트 세트의 속성은 전파되지 않습니다. 옵션 상속 동작은 `Test`가 제공하는 스택 인프라를 사용하여 패키지에서 구현할 수 있습니다.

기본 `AbstractTestSet` 하위 유형을 정의하는 것은 다음과 같을 수 있습니다:

```julia
import Test: Test, record, finish
using Test: AbstractTestSet, Result, Pass, Fail, Error
using Test: get_testset_depth, get_testset
struct CustomTestSet <: Test.AbstractTestSet
    description::AbstractString
    foo::Int
    results::Vector
    # constructor takes a description string and options keyword arguments
    CustomTestSet(desc; foo=1) = new(desc, foo, [])
end

record(ts::CustomTestSet, child::AbstractTestSet) = push!(ts.results, child)
record(ts::CustomTestSet, res::Result) = push!(ts.results, res)
function finish(ts::CustomTestSet)
    # just record if we're not the top-level parent
    if get_testset_depth() > 0
        record(get_testset(), ts)
        return ts
    end

    # so the results are printed if we are at the top level
    Test.print_test_results(ts)
    return ts
end
```

그리고 그 테스트 세트를 사용하는 모습은 다음과 같습니다:

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

사용자 정의 테스트 세트를 사용하고 기록된 결과가 외부 기본 테스트 세트의 일부로 인쇄되도록 하려면 `Test.get_test_counts`도 정의해야 합니다. 이는 다음과 같이 보일 수 있습니다:

```julia
using Test: AbstractTestSet, Pass, Fail, Error, Broken, get_test_counts, TestCounts, format_duration

function Test.get_test_counts(ts::CustomTestSet)
    passes, fails, errors, broken = 0, 0, 0, 0
    # cumulative results
    c_passes, c_fails, c_errors, c_broken = 0, 0, 0, 0

    for t in ts.results
        # count up results
        isa(t, Pass)   && (passes += 1)
        isa(t, Fail)   && (fails  += 1)
        isa(t, Error)  && (errors += 1)
        isa(t, Broken) && (broken += 1)
        # handle children
        if isa(t, AbstractTestSet)
            tc = get_test_counts(t)::TestCounts
            c_passes += tc.passes + tc.cumulative_passes
            c_fails  += tc.fails + tc.cumulative_fails
            c_errors += tc.errors + tc.cumulative_errors
            c_broken += tc.broken + tc.cumulative_broken
        end
    end
    # get a duration, if we have one
    duration = format_duration(ts)
    return TestCounts(true, passes, fails, errors, broken, c_passes, c_fails, c_errors, c_broken, duration)
end
```

```@docs
Test.TestCounts
Test.get_test_counts
Test.format_duration
Test.print_test_results
```

## Test utilities

```@docs
Test.GenericArray
Test.GenericDict
Test.GenericOrder
Test.GenericSet
Test.GenericString
Test.detect_ambiguities
Test.detect_unbound_args
```

## Workflow for Testing Packages

이전 섹션에서 사용 가능한 도구를 사용하여 패키지를 생성하고 테스트를 추가하는 잠재적인 워크플로우는 다음과 같습니다.

### Generating an Example Package

이 워크플로우에서는 `Example`이라는 패키지를 생성할 것입니다:

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

테스트 패키지를 위한 가장 중요한 요구 사항은 테스트할 기능이 있는 것입니다. 이를 위해, 우리는 테스트할 수 있는 몇 가지 간단한 함수를 `Example`에 추가할 것입니다. 다음을 `src/Example.jl`에 추가하세요:

```julia
module Example

function greet()
    "Hello world!"
end

function simple_add(a, b)
    a + b
end

function type_multiply(a::Float64, b::Float64)
    a * b
end

export greet, simple_add, type_multiply

end
```

### Creating a Test Environment

`Example` 패키지의 루트에서 `test` 디렉토리로 이동한 후, 그곳에서 새로운 환경을 활성화하고 `Test` 패키지를 환경에 추가합니다:

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

이제 `Example`에 테스트를 추가할 준비가 되었습니다. 실행할 테스트 세트를 포함하는 `runtests.jl`라는 파일을 `test` 디렉토리 내에 만드는 것이 표준 관행입니다. `test` 디렉토리 내에 해당 파일을 생성하고 다음 코드를 추가하세요:

```julia
using Example
using Test

@testset "Example tests" begin

    @testset "Math tests" begin
        include("math_tests.jl")
    end

    @testset "Greeting tests" begin
        include("greeting_tests.jl")
    end
end
```

우리는 `math_tests.jl`와 `greeting_tests.jl`라는 두 개의 포함된 파일을 생성하고, 그 안에 몇 가지 테스트를 추가해야 합니다.

> **참고:** `test` 환경의 `Project.toml`에 `Example`을 추가할 필요가 없다는 점에 주목하세요. 이는 줄리아의 테스트 시스템의 장점으로, 여러분은 [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/)를 사용할 수 있습니다.


#### Writing Tests for `math_tests.jl`

`Test.jl`에 대한 우리의 지식을 바탕으로, `math_tests.jl`에 추가할 수 있는 몇 가지 예제 테스트는 다음과 같습니다:

```julia
@testset "Testset 1" begin
    @test 2 == simple_add(1, 1)
    @test 3.5 == simple_add(1, 2.5)
        @test_throws MethodError simple_add(1, "A")
        @test_throws MethodError simple_add(1, 2, 3)
end

@testset "Testset 2" begin
    @test 1.0 == type_multiply(1.0, 1.0)
        @test isa(type_multiply(2.0, 2.0), Float64)
    @test_throws MethodError type_multiply(1, 2.5)
end
```

#### Writing Tests for `greeting_tests.jl`

`Test.jl`에 대한 우리의 지식을 바탕으로, `greeting_tests.jl`에 추가할 수 있는 몇 가지 예제 테스트는 다음과 같습니다:

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

이제 `test`에 테스트와 `runtests.jl` 스크립트를 추가했으므로, `Example` 패키지 환경의 루트로 돌아가서 `Example` 환경을 다시 활성화하여 `Example` 패키지를 테스트할 수 있습니다:

```julia
shell> cd ..
pkg> activate .
```

거기서 우리는 다음과 같이 테스트 스위트를 실행할 수 있습니다:

```julia
(Example) pkg> test
     Testing Example
      Status `/tmp/jl_Yngpvy/Project.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [8dfed614] Test `@stdlib/Test`
      Status `/tmp/jl_Yngpvy/Manifest.toml`
  [fa318bd2] Example v0.1.0 `/home/src/Projects/tmp/errata/Example`
  [2a0f44e3] Base64 `@stdlib/Base64`
  [b77e0a4c] InteractiveUtils `@stdlib/InteractiveUtils`
  [56ddb016] Logging `@stdlib/Logging`
  [d6f4376e] Markdown `@stdlib/Markdown`
  [9a3f8284] Random `@stdlib/Random`
  [ea8e919c] SHA `@stdlib/SHA`
  [9e88b42a] Serialization `@stdlib/Serialization`
  [8dfed614] Test `@stdlib/Test`
     Testing Running tests...
Test Summary: | Pass  Total
Example tests |    9      9
     Testing Example tests passed
```

모든 것이 올바르게 진행되었다면, 위와 유사한 출력을 볼 수 있어야 합니다. `Test.jl`을 사용하면 패키지에 대해 더 복잡한 테스트를 추가할 수 있지만, 이는 이상적으로 개발자들이 자신이 만든 패키지의 테스트를 시작하는 방법을 안내하는 방향으로 나아가야 합니다.

```@meta
DocTestSetup = nothing
```

### Code Coverage

테스트 중 코드 커버리지 추적은 `pkg> test --coverage` 플래그를 사용하여 활성화할 수 있습니다 (또는 더 낮은 수준에서 [`--code-coverage`](@ref command-line-interface) 줄리아 인수를 사용하여). 이는 [julia-runtest](https://github.com/julia-actions/julia-runtest) GitHub 액션에서 기본적으로 활성화되어 있습니다.

To evaluate coverage either manually inspect the `.cov` files that are generated beside the source files locally, or in CI use the [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub action.

!!! compat "Julia 1.11"
    Julia 1.11부터는 패키지 사전 컴파일 단계에서 커버리지가 수집되지 않습니다.

