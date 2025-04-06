```
符号
```

用于表示解析的 julia 代码 (ASTs) 中标识符的对象类型。也常用作名称或标签来标识实体（例如，作为字典键）。可以使用 `:` 引用运算符输入 `Symbol`：

```jldoctest
julia> :name
:name

julia> typeof(:name)
Symbol

julia> x = 42
42

julia> eval(:x)
42
```

`Symbol` 还可以通过调用构造函数 `Symbol(x...)` 从字符串或其他值构造。

`Symbol` 是不可变的，其实现为所有具有相同名称的 `Symbol` 复用相同的对象。

与字符串不同，`Symbol` 是“原子”或“标量”实体，不支持对字符的迭代。
