```
@test_broken ex
@test_broken f(args...) key=val ...
```

表示一个应该通过但当前始终失败的测试。测试表达式 `ex` 是否评估为 `false` 或导致异常。如果是，则返回 `Broken` `Result`，如果表达式评估为 `true`，则返回 `Error` `Result`。这等同于 [`@test ex broken=true`](@ref @test)。

`@test_broken f(args...) key=val...` 的形式与 `@test` 宏的用法相同。

# 示例

```jldoctest
julia> @test_broken 1 == 2
测试失败
  表达式: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
测试失败
  表达式: ==(1, 2, atol = 0.1)
```
