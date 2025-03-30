```
unsafe_pointer_to_objref(p::Ptr)
```

将 `Ptr` 转换为对象引用。假设指针指向一个有效的堆分配的 Julia 对象。如果不是这种情况，将导致未定义的行为，因此此函数被认为是“安全性不确定”，应谨慎使用。

另见 [`pointer_from_objref`](@ref)。
