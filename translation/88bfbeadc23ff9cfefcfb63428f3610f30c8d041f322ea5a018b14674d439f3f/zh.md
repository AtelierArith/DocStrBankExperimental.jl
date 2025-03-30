```
pointer(array [, index])
```

获取数组或字符串的原生地址，选项上可以指定给定位置 `index`。

此函数是“非安全”的。请小心确保在使用此指针的整个过程中，Julia 对 `array` 的引用存在。应使用 [`GC.@preserve`](@ref) 宏来保护 `array` 参数在给定代码块内不被垃圾回收。

调用 [`Ref(array[, index])`](@ref Ref) 通常比此函数更可取，因为它保证了有效性。
