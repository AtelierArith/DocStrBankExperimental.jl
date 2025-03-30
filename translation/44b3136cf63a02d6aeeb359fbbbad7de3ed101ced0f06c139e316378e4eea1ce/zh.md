```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Test/docs/src/index.md"
```

# Unit Testing

```@meta
DocTestSetup = :(using Test)
```

## Testing Base Julia

Julia 正在快速发展，并且拥有一个广泛的测试套件，以验证多个平台上的功能。如果您从源代码构建 Julia，可以使用 `make test` 运行此测试套件。在二进制安装中，您可以使用 `Base.runtests()` 运行测试套件。

```@docs
Base.runtests
```

## Basic Unit Tests

`Test` 模块提供简单的 *单元测试* 功能。单元测试是一种通过检查结果是否符合预期来验证代码正确性的方法。它可以帮助确保在您进行更改后代码仍然正常工作，并且可以在开发时用作指定代码完成时应具有的行为的方式。您可能还想查看 [adding tests to your Julia Package](https://pkgdocs.julialang.org/dev/creating-packages/#Adding-tests-to-the-package) 的文档。

简单的单元测试可以使用 `@test` 和 `@test_throws` 宏进行：

```@docs
Test.@test
Test.@test_throws
```

例如，假设我们想检查我们的新函数 `foo(x)` 是否按预期工作：

```jldoctest testfoo
julia> using Test

julia> foo(x) = length(x)^2
foo (generic function with 1 method)
```

如果条件为真，则返回 `Pass`：

```jldoctest testfoo
julia> @test foo("bar") == 9
Test Passed

julia> @test foo("fizz") >= 10
Test Passed
```

如果条件为假，则返回 `Fail` 并抛出异常：

```jldoctest testfoo
julia> @test foo("f") == 20
Test Failed at none:1
  Expression: foo("f") == 20
   Evaluated: 1 == 20

ERROR: There was an error during testing
```

如果条件无法评估，因为抛出了一个异常，在这种情况下，因为符号没有定义 `length`，将返回一个 `Error` 对象并抛出一个异常：

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

如果我们期望评估一个表达式 *应该* 抛出一个异常，那么我们可以使用 `@test_throws` 来检查这一点：

```jldoctest testfoo
julia> @test_throws MethodError foo(:cat)
Test Passed
      Thrown: MethodError
```

## Working with Test Sets

通常会使用大量测试来确保函数在一系列输入下正常工作。如果测试失败，默认行为是立即抛出异常。然而，通常更可取的是先运行其余的测试，以更好地了解被测试代码中有多少错误。

!!! note
    `@testset` 在运行其中的测试时会创建一个自己的局部作用域。


`@testset` 宏可以用来将测试分组为 *集合*。测试集合中的所有测试都会被运行，并且在测试集合结束时会打印一个摘要。如果任何测试失败，或者由于错误无法评估，测试集合将抛出 `TestSetException`。

```@docs
Test.@testset
Test.TestSetException
```

我们可以将 `foo(x)` 函数的测试放入一个测试集：

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> @testset "Foo Tests" begin
           @test foo("a")   == 1
           @test foo("ab")  == 4
           @test foo("abc") == 9
       end;
Test Summary: | Pass  Total  Time
Foo Tests     |    3      3  0.0s
```

测试集也可以嵌套：

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

以及调用函数：

```jldoctest testfoo; filter = r"[0-9\.]+s"
julia> f(x) = @test isone(x)
f (generic function with 1 method)

julia> @testset f(1);
Test Summary: | Pass  Total  Time
f             |    1      1  0.0s
```

这可以用于允许测试集的因式分解，使得通过运行相关函数来运行单个测试集变得更容易。请注意，在函数的情况下，测试集将被赋予被调用函数的名称。如果嵌套测试集没有失败，如这里发生的那样，它将在摘要中被隐藏，除非传递了 `verbose=true` 选项：

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

如果我们确实有测试失败，只有失败测试集的详细信息会被显示：

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

可以使用 [`@test_logs`](@ref) 宏来测试日志语句，或者使用 [`TestLogger`](@ref)。

```@docs
Test.@test_logs
Test.TestLogger
Test.LogRecord
```

## Other Test Macros

由于对浮点值的计算可能不精确，您可以使用 `@test a ≈ b` 进行近似相等检查（其中 `≈` 是通过键入 `\approx` 的选项完成来输入的，是 [`isapprox`](@ref) 函数），或者直接使用 `4d61726b646f776e2e436f64652822222c20226973617070726f782229_40726566`。

```jldoctest
julia> @test 1 ≈ 0.999999999
Test Passed

julia> @test 1 ≈ 0.999999
Test Failed at none:1
  Expression: 1 ≈ 0.999999
   Evaluated: 1 ≈ 0.999999

ERROR: There was an error during testing
```

您可以通过在 `≈` 比较后设置 `isapprox` 的 `rtol` 和 `atol` 关键字参数来指定相对和绝对容忍度：

```jldoctest
julia> @test 1 ≈ 0.999999  rtol=1e-5
Test Passed
```

请注意，这不是 `≈` 的特定功能，而是 `@test` 宏的一个通用特性：`@test a <op> b key=val` 被宏转换为 `@test op(a, b, key=val)`。然而，这对于 `≈` 测试特别有用。

```@docs
Test.@inferred
Test.@test_deprecated
Test.@test_warn
Test.@test_nowarn
```

## Broken Tests

如果一个测试持续失败，可以将其更改为使用 `@test_broken` 宏。这将标记该测试为 `Broken`，如果测试继续失败，并在测试成功时通过 `Error` 提醒用户。

```@docs
Test.@test_broken
```

`@test_skip` 也可用于跳过测试而不进行评估，但在测试集报告中计入跳过的测试。该测试将不会运行，但会给出一个 `Broken` `Result`。

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

包可以通过实现 `record` 和 `finish` 方法来创建自己的 `AbstractTestSet` 子类型。子类型应具有一个接受描述字符串的单参数构造函数，任何选项都作为关键字参数传递。

```@docs
Test.record
Test.finish
```

`Test` 负责维护在执行时嵌套测试集的堆栈，但任何结果的累积都是 `AbstractTestSet` 子类型的责任。您可以通过 `get_testset` 和 `get_testset_depth` 方法访问此堆栈。请注意，这些函数未被导出。

```@docs
Test.get_testset
Test.get_testset_depth
```

`Test` 还确保嵌套的 `@testset` 调用使用与其父级相同的 `AbstractTestSet` 子类型，除非明确设置。它不会传播测试集的任何属性。选项继承行为可以通过使用 `Test` 提供的堆栈基础设施由包实现。

定义一个基本的 `AbstractTestSet` 子类型可能看起来像：

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

并且使用该测试集看起来像：

```julia
@testset CustomTestSet foo=4 "custom testset inner 2" begin
    # this testset should inherit the type, but not the argument.
    @testset "custom testset inner" begin
        @test true
    end
end
```

为了使用自定义测试集并将记录的结果作为任何外部默认测试集的一部分打印出来，还需要定义 `Test.get_test_counts`。这可能看起来像这样：

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

使用我们在前面部分中可用的工具，以下是创建一个包并向其添加测试的潜在工作流程。

### Generating an Example Package

对于这个工作流程，我们将创建一个名为 `Example` 的包：

```julia
pkg> generate Example
shell> cd Example
shell> mkdir test
pkg> activate .
```

### Creating Sample Functions

测试一个包的首要要求是拥有可测试的功能。为此，我们将向 `Example` 添加一些简单的函数，以便进行测试。将以下内容添加到 `src/Example.jl`：

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

从 `Example` 包的根目录中，导航到 `test` 目录，在那里激活一个新环境，并将 `Test` 包添加到该环境中：

```julia
shell> cd test
pkg> activate .
(test) pkg> add Test
```

### Testing Our Package

现在，我们准备为 `Example` 添加测试。标准做法是在 `test` 目录中创建一个名为 `runtests.jl` 的文件，其中包含我们想要运行的测试集。请在 `test` 目录中创建该文件，并添加以下代码：

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

我们需要创建这两个包含的文件，`math_tests.jl` 和 `greeting_tests.jl`，并向它们添加一些测试。

> **注意：** 请注意，我们不需要在 `test` 环境的 `Project.toml` 中指定添加 `Example`。这是 Julia 测试系统的一个好处，您可以 [read about more here](https://pkgdocs.julialang.org/dev/creating-packages/)。


#### Writing Tests for `math_tests.jl`

使用我们对 `Test.jl` 的了解，这里有一些我们可以添加到 `math_tests.jl` 的示例测试：

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

使用我们对 `Test.jl` 的了解，以下是我们可以添加到 `greeting_tests.jl` 的一些示例测试：

```julia
@testset "Testset 3" begin
    @test "Hello world!" == greet()
    @test_throws MethodError greet("Antonia")
end
```

### Testing Our Package

现在我们已经在 `test` 中添加了我们的测试和 `runtests.jl` 脚本，我们可以通过返回到 `Example` 包环境的根目录并重新激活 `Example` 环境来测试我们的 `Example` 包：

```julia
shell> cd ..
pkg> activate .
```

从那里，我们终于可以按如下方式运行我们的测试套件：

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

如果一切顺利，你应该会看到与上面类似的输出。使用 `Test.jl`，可以为包添加更复杂的测试，但这应该理想地指引开发者如何开始测试他们自己创建的包。

```@meta
DocTestSetup = nothing
```

### Code Coverage

在测试期间，可以使用 `pkg> test --coverage` 标志启用代码覆盖率跟踪（或使用 [`--code-coverage`](@ref command-line-interface) julia 参数在更低级别启用）。在 [julia-runtest](https://github.com/julia-actions/julia-runtest) GitHub 操作中，默认启用此功能。

要评估覆盖率，可以手动检查生成在源文件旁边的 `.cov` 文件，或者在 CI 中使用 [julia-processcoverage](https://github.com/julia-actions/julia-processcoverage) GitHub 操作。

!!! compat "Julia 1.11"
    自 Julia 1.11 起，覆盖率不再在包的预编译阶段收集。

