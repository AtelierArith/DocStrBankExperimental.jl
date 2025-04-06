`BroadcastStyle` 是一个抽象类型和特征函数，用于确定对象在广播下的行为。 `BroadcastStyle(typeof(x))` 返回与 `x` 相关联的样式。要自定义类型的广播行为，可以通过定义类型/方法对来声明样式

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

然后编写操作 `Broadcasted{MyContainerStyle}` 的方法（至少 [`similar`](@ref)）。还有几个预定义的 `BroadcastStyle` 子类型，您可以利用它们；有关更多信息，请参见 [Interfaces chapter](@ref man-interfaces-broadcasting)。
