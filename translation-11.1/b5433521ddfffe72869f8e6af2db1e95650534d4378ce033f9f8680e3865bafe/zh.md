```
@debug 消息  [key=value | value ...]
@info  消息  [key=value | value ...]
@warn  消息  [key=value | value ...]
@error 消息  [key=value | value ...]

@logmsg 级别 消息 [key=value | value ...]

创建一个包含信息性 `消息` 的日志记录。为了方便，定义了四个日志宏 `@debug`、`@info`、`@warn` 和 `@error`，它们在标准严重性级别 `Debug`、`Info`、`Warn` 和 `Error` 下进行日志记录。`@logmsg` 允许 `级别` 被程序化设置为任何 `LogLevel` 或自定义日志级别类型。

`消息` 应该是一个表达式，评估为一个字符串，作为日志事件的可读描述。根据惯例，当呈现时，这个字符串将被格式化为 markdown。

可选的 `key=value` 对列表支持任意用户定义的元数据，这些元数据将作为日志记录的一部分传递给日志后端。如果只提供了一个 `value` 表达式，将使用 [`Symbol`](@ref) 生成一个表示该表达式的键。例如，`x` 变为 `x=x`，而 `foo(10)` 变为 `Symbol("foo(10)")=foo(10)`。要展开一组键值对，请使用正常的展开语法，`@info "blah" kws...`。

有一些键允许覆盖自动生成的日志数据：

  * `_module=mod` 可用于指定与消息源位置不同的原始模块。
  * `_group=symbol` 可用于覆盖消息组（这通常是从源文件的基本名称派生的）。
  * `_id=symbol` 可用于覆盖自动生成的唯一消息标识符。如果需要非常紧密地关联在不同源行生成的消息，这非常有用。
  * `_file=string` 和 `_line=integer` 可用于覆盖日志消息的明显源位置。

还有一些具有约定含义的键值对：

  * `maxlog=integer` 应作为提示传递给后端，表示消息最多应显示 `maxlog` 次。
  * `exception=ex` 应用于与日志消息一起传输异常，通常与 `@error` 一起使用。可以使用元组 `exception=(ex,bt)` 附加相关的回溯 `bt`。

# 示例

```

julia @debug "详细调试信息。默认情况下不可见" @info  "一条信息性消息" @warn  "有些事情很奇怪。你应该注意" @error "发生了一个非致命错误"

x = 10 @info "附加到消息的一些变量" x a=42.0

@debug begin     sA = sum(A)     "sum(A) = :sA 是一个昂贵的操作，仅在 `shouldlog` 返回 true 时评估" end

for i=1:10000     @info "使用默认后端，你将只看到 (i = :i) 十次"  maxlog=10     @debug "算法1" i progress=i/10000 end ```
