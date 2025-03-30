```
@test ex
@test f(args...) key=val ...
@test ex broken=true
@test ex skip=true
```

测试表达式 `ex` 是否评估为 `true`。如果在 `@testset` 内执行，如果是，则返回 `Pass` `Result`，如果为 `false`，则返回 `Fail` `Result`，如果无法评估，则返回 `Error` `Result`。如果在 `@testset` 外执行，则抛出异常，而不是返回 `Fail` 或 `Error`。

# 示例

```jldoctest
julia> @test true
测试通过

julia> @test [1, 2] + [2, 1] == [3, 3]
测试通过
```

`@test f(args...) key=val...` 形式等同于写 `@test f(args..., key=val...)`，这在表达式使用中缀语法进行近似比较时非常有用：

```jldoctest
julia> @test π ≈ 3.14 atol=0.01
测试通过
```

这等同于更丑陋的测试 `@test ≈(π, 3.14, atol=0.01)`。除非第一个是调用表达式，其余是赋值（`k=v`），否则提供多个表达式是错误的。

您可以为 `key=val` 参数使用任何键，除了 `broken` 和 `skip`，它们在 `@test` 的上下文中具有特殊含义：

  * `broken=cond` 表示一个应该通过但当前在 `cond==true` 时始终失败的测试。测试表达式 `ex` 是否评估为 `false` 或导致异常。如果是，则返回 `Broken` `Result`，如果表达式评估为 `true`，则返回 `Error` `Result`。常规的 `@test ex` 在 `cond==false` 时被评估。
  * `skip=cond` 标记一个不应执行但在 `cond==true` 时应包含在测试摘要报告中的测试，作为 `Broken`。这对于间歇性失败的测试或尚未实现的功能的测试非常有用。常规的 `@test ex` 在 `cond==false` 时被评估。

# 示例

```jldoctest
julia> @test 2 + 2 ≈ 6 atol=1 broken=true
测试已损坏
  表达式: ≈(2 + 2, 6, atol = 1)

julia> @test 2 + 2 ≈ 5 atol=1 broken=false
测试通过

julia> @test 2 + 2 == 5 skip=true
测试已损坏
  跳过: 2 + 2 == 5

julia> @test 2 + 2 == 4 skip=false
测试通过
```

!!! compat "Julia 1.7"
    `broken` 和 `skip` 关键字参数需要至少 Julia 1.7。

