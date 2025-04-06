```
pointer_from_objref(x)
```

获取Julia对象的内存地址作为`Ptr`。生成的`Ptr`的存在不会保护对象不被垃圾回收，因此您必须确保在使用`Ptr`的整个过程中对象保持被引用。

此函数不能在不可变对象上调用，因为它们没有稳定的内存地址。

另请参见[`unsafe_pointer_to_objref`](@ref)。
