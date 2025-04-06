```
unsafe_wrap(Array, pointer::Ptr{T}, dims; own = false)
```

在给定的 `pointer` 地址上将一个 Julia `Array` 对象包装在数据周围，而不进行复制。指针元素类型 `T` 决定了数组元素类型。`dims` 可以是一个整数（用于一维数组）或一个数组维度的元组。`own` 可选地指定 Julia 是否应当拥有内存，当数组不再被引用时调用 `free` 释放指针。

此函数被标记为“unsafe”，因为如果 `pointer` 不是有效的内存地址，且数据长度不匹配，则会崩溃。与 [`unsafe_load`](@ref) 和 [`unsafe_store!`](@ref) 不同，程序员还需确保底层数据不会通过两种不同元素类型的数组进行访问，这类似于 C 语言中的严格别名规则。
