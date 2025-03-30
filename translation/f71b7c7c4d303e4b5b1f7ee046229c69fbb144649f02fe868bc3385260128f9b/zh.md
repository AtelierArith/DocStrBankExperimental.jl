```
IOContext(io::IO, KV::Pair...)
```

创建一个 `IOContext`，它包装了给定的流，并将指定的 `key=>value` 对添加到该流的属性中（注意 `io` 本身可以是一个 `IOContext`）。

  * 使用 `(key => value) in io` 来查看这个特定的组合是否在属性集中
  * 使用 `get(io, key, default)` 来检索特定键的最新值

以下属性是常用的：

  * `:compact`：布尔值，指定值应该更紧凑地打印，例如，数字应该用更少的数字打印。当打印数组元素时设置此项。`:compact` 输出不应包含换行符。
  * `:limit`：布尔值，指定容器应该被截断，例如，用 `…` 替代大多数元素。
  * `:displaysize`：一个 `Tuple{Int,Int}`，给出用于文本输出的行和列的大小。这可以用来覆盖调用函数的显示大小，但要获取屏幕的大小，请使用 `displaysize` 函数。
  * `:typeinfo`：一个 `Type`，表征关于即将显示的对象类型的已打印信息。这在显示同一类型的对象集合时特别有用，以避免冗余的类型信息（例如，`[Float16(0)]` 可以显示为 "Float16[0.0]" 而不是 "Float16[Float16(0.0)]"：在显示数组元素时，`:typeinfo` 属性将被设置为 `Float16`）。
  * `:color`：布尔值，指定是否支持/期望 ANSI 颜色/转义代码。默认情况下，这由 `io` 是否是兼容终端以及在启动 `julia` 时的任何 `--color` 命令行标志决定。

# 示例

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generic function with 1 method)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```
