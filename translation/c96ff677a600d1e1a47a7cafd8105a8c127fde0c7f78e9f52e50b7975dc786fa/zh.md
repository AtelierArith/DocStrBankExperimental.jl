```
@test_throws exception expr
```

测试表达式 `expr` 是否抛出 `exception`。异常可以指定类型、字符串、正则表达式或在显示的错误消息中出现的字符串列表、匹配函数或值（将通过比较字段进行相等性测试）。请注意，`@test_throws` 不支持尾随关键字形式。

!!! compat "Julia 1.8"
    指定除类型或值以外的任何内容作为 `exception` 的能力需要 Julia v1.8 或更高版本。


# 示例

```jldoctest
julia> @test_throws BoundsError [1, 2, 3][4]
测试通过
      抛出: BoundsError

julia> @test_throws DimensionMismatch [1, 2, 3] + [1, 2]
测试通过
      抛出: DimensionMismatch

julia> @test_throws "Try sqrt(Complex" sqrt(-1)
测试通过
     消息: "DomainError with -1.0:\nsqrt 被调用时使用了负实数参数，但仅在使用复数参数时才会返回复数结果。尝试使用 sqrt(Complex(x))。"
```

在最后一个示例中，除了匹配单个字符串外，还可以使用以下方式进行匹配：

  * `["Try", "Complex"]`（字符串列表）
  * `r"Try sqrt\([Cc]omplex"`（正则表达式）
  * `str -> occursin("complex", str)`（匹配函数）
