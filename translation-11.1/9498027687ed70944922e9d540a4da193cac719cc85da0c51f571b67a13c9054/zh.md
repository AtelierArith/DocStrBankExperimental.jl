```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

从内存对象和一个偏移索引（基于1的索引，可以是负数）构造一个 `GenericMemoryRef`。这总是返回一个有效的对象，如果不可能（因为索引会导致超出基础内存的范围），则会抛出错误。
