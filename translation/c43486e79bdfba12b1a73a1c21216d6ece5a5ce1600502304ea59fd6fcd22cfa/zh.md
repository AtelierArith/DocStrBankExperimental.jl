```
@test_skip ex
@test_skip f(args...) key=val ...
```

标记一个不应执行但应包含在测试摘要报告中的测试，状态为 `Broken`。这对于间歇性失败的测试或尚未实现功能的测试非常有用。这相当于 [`@test ex skip=true`](@ref @test)。

`@test_skip f(args...) key=val...` 的形式与 `@test` 宏的用法相同。

# 示例

```jldoctest
julia> @test_skip 1 == 2
测试已损坏
  跳过: 1 == 2

julia> @test_skip 1 == 2 atol=0.1
测试已损坏
  跳过: ==(1, 2, atol = 0.1)
```
