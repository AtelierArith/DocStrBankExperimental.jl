```
@testset [CustomTestSet] [options...] ["描述"] begin test_ex end
@testset [CustomTestSet] [options...] ["描述 $v"] for v in itr test_ex end
@testset [CustomTestSet] [options...] ["描述 $v, $w"] for v in itrv, w in itrw test_ex end
@testset [CustomTestSet] [options...] ["描述"] test_func()
@testset let v = v, w = w; test_ex; end
```

# 使用 begin/end 或函数调用

当使用 @testset 时，使用 begin/end 或单个函数调用，宏会启动一个新的测试集来评估给定的表达式。

如果没有给定自定义测试集类型，则默认为创建一个 `DefaultTestSet`。`DefaultTestSet` 记录所有结果，如果有任何 `Fail` 或 `Error`，则在顶层（非嵌套）测试集的末尾抛出异常，并附上测试结果的摘要。

可以给定任何自定义测试集类型（`AbstractTestSet` 的子类型），它也将用于任何嵌套的 `@testset` 调用。给定的选项仅应用于给定的测试集。默认测试集类型接受三个布尔选项：

  * `verbose`：如果为 `true`，即使所有嵌套测试集都通过，结果摘要也会显示（默认值为 `false`）。
  * `showtiming`：如果为 `true`，则显示每个显示的测试集的持续时间（默认值为 `true`）。
  * `failfast`：如果为 `true`，任何测试失败或错误将导致测试集和任何子测试集立即返回（默认值为 `false`）。这也可以通过环境变量 `JULIA_TEST_FAILFAST` 全局设置。

!!! compat "Julia 1.8"
    `@testset test_func()` 至少需要 Julia 1.8。


!!! compat "Julia 1.9"
    `failfast` 至少需要 Julia 1.9。


描述字符串接受来自循环索引的插值。如果没有提供描述，则根据变量构造一个。如果提供了函数调用，则将使用其名称。显式描述字符串会覆盖此行为。

默认情况下，`@testset` 宏将返回测试集对象本身，尽管此行为可以在其他测试集类型中自定义。如果使用了 `for` 循环，则宏会收集并返回 `finish` 方法的返回值列表，默认情况下将返回每次迭代中使用的测试集对象列表。

在 `@testset` 的主体执行之前，会隐式调用 `Random.seed!(seed)`，其中 `seed` 是全局随机数生成器的当前种子。此外，在主体执行后，全局随机数生成器的状态将恢复到 `@testset` 之前的状态。这旨在在失败的情况下简化可重现性，并允许无缝重新排列 `@testset`，而不考虑它们对全局随机数生成器状态的副作用。

## 示例

```jldoctest; filter = r"trigonometric identities |    4      4  [0-9\.]+s"
julia> @testset "三角恒等式" begin
           θ = 2/3*π
           @test sin(-θ) ≈ -sin(θ)
           @test cos(-θ) ≈ cos(θ)
           @test sin(2θ) ≈ 2*sin(θ)*cos(θ)
           @test cos(2θ) ≈ cos(θ)^2 - sin(θ)^2
       end;
测试摘要:            | 通过  总计  时间
三角恒等式 |    4      4  0.2s
```

# `@testset for`

当使用 `@testset for` 时，宏会为提供的循环的每次迭代启动一个新的测试。每个测试集的语义与 `begin/end` 情况是相同的（就像在每次循环迭代中使用一样）。

# `@testset let`

当使用 `@testset let` 时，宏会启动一个 *透明* 测试集，将给定对象作为上下文对象添加到其中的任何失败测试。这在对一个较大对象执行一组相关测试时非常有用，并且希望在任何单个测试失败时打印这个较大对象。透明测试集不会在测试集层次结构中引入额外的嵌套级别，并直接传递给父测试集（上下文对象附加到任何失败的测试中）。

!!! compat "Julia 1.9"
    `@testset let` 至少需要 Julia 1.9。


!!! compat "Julia 1.10"
    从 Julia 1.10 开始支持多个 `let` 赋值。


## 示例

```jldoctest
julia> @testset let logi = log(im)
           @test imag(logi) == π/2
           @test !iszero(real(logi))
       end
测试失败于 none:3
  表达式: !(iszero(real(logi)))
     上下文: logi = 0.0 + 1.5707963267948966im

错误: 测试期间发生错误

julia> @testset let logi = log(im), op = !iszero
           @test imag(logi) == π/2
           @test op(real(logi))
       end
测试失败于 none:3
  表达式: op(real(logi))
     上下文: logi = 0.0 + 1.5707963267948966im
              op = !iszero

错误: 测试期间发生错误
```
