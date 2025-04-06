```
@test_logs [log_patterns...] [keywords] 表达式
```

使用 `collect_test_logs` 收集由 `表达式` 生成的日志记录列表，检查它们是否与序列 `log_patterns` 匹配，并返回 `表达式` 的值。`keywords` 提供了一些简单的日志记录过滤：`min_level` 关键字控制将为测试收集的最低日志级别，`match_mode` 关键字定义将如何进行匹配（默认的 `:all` 检查所有日志和模式是否逐对匹配；使用 `:any` 检查模式是否至少在序列中的某个地方匹配一次。）

最有用的日志模式是简单的元组，形式为 `(level,message)`。可以使用不同数量的元组元素来匹配其他日志元数据，对应于通过 `handle_message` 函数传递给 `AbstractLogger` 的参数：`(level,message,module,group,id,file,line)`。存在的元素将默认使用 `==` 与日志记录字段逐对匹配，特殊情况是可以使用 `Symbol` 作为标准日志级别，而模式中的 `Regex` 将使用 `occursin` 匹配字符串或 Symbol 字段。

# 示例

考虑一个记录警告和几个调试消息的函数：

```
function foo(n)
    @info "Doing foo with n=$n"
    for i=1:n
        @debug "Iteration $i"
    end
    42
end
```

我们可以使用以下方式测试信息消息：

```
@test_logs (:info,"Doing foo with n=2") foo(2)
```

如果我们还想测试调试消息，则需要使用 `min_level` 关键字启用它们：

```
using Logging
@test_logs (:info,"Doing foo with n=2") (:debug,"Iteration 1") (:debug,"Iteration 2") min_level=Logging.Debug foo(2)
```

如果您想测试某些特定消息的生成，同时忽略其余消息，可以将关键字 `match_mode=:any` 设置为：

```
using Logging
@test_logs (:info,) (:debug,"Iteration 42") min_level=Logging.Debug match_mode=:any foo(100)
```

该宏可以与 `@test` 链接，以测试返回值：

```
@test (@test_logs (:info,"Doing foo with n=2") foo(2)) == 42
```

如果您想测试没有警告的情况，可以省略指定日志模式，并相应地设置 `min_level`：

```
# 测试当记录器级别为警告时，表达式不记录任何消息：
@test_logs min_level=Logging.Warn @info("Some information") # 通过
@test_logs min_level=Logging.Warn @warn("Some information") # 失败
```

如果您想测试在 [`stderr`](@ref) 中没有由 `@warn` 生成的警告（或错误消息），请参见 [`@test_nowarn`](@ref)。
