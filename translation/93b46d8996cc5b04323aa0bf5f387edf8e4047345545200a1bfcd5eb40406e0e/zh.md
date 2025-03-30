```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

将 `x` 赋值给可组合类型 `value` 中的命名字段。`value` 必须是可变的，`x` 必须是 `fieldtype(typeof(value), name)` 的子类型。此外，可以为此操作指定一个顺序。如果字段被声明为 `@atomic`，则此规范是强制性的。否则，如果未声明为 `@atomic`，则如果指定，必须为 `:not_atomic`。另请参见 [`setproperty!`](@ref Base.setproperty!)。

# 示例

```jldoctest
julia> mutable struct MyMutableStruct
           field::Int
       end

julia> a = MyMutableStruct(1);

julia> setfield!(a, :field, 2);

julia> getfield(a, :field)
2

julia> a = 1//2
1//2

julia> setfield!(a, :num, 3);
ERROR: setfield!: immutable struct of type Rational cannot be changed
```
