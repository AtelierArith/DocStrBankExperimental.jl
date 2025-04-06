```
@test_deprecated [pattern] 表达式
```

当 `--depwarn=yes` 时，测试 `表达式` 是否发出弃用警告，并返回 `表达式` 的值。日志消息字符串将与默认的 `r"deprecated"i` 的 `pattern` 进行匹配。

当 `--depwarn=no` 时，简单地返回执行 `表达式` 的结果。当 `--depwarn=error` 时，检查是否抛出 `ErrorException`。

# 示例

```
# 在 julia 0.7 中已弃用
@test_deprecated num2hex(1)

# 返回的值可以通过与 @test 链接进行测试：
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
