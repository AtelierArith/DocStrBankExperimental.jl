```
===(x,y) -> Bool
≡(x,y) -> Bool
```

确定 `x` 和 `y` 是否相同，意思是没有程序能够区分它们。首先比较 `x` 和 `y` 的类型。如果类型相同，则可变对象通过内存地址进行比较，而不可变对象（例如数字）则通过位级内容进行比较。这个函数有时被称为 "egal"。它总是返回一个 `Bool` 值。

# 示例

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a == b
true

julia> a === b
false

julia> a === a
true
```
