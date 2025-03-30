```
WeakKeyDict([itr])
```

`WeakKeyDict()` 构造一个哈希表，其中键是对可能被垃圾回收的对象的弱引用，即使在哈希表中被引用时也可能被回收。

有关更多帮助，请参见 [`Dict`](@ref)。请注意，与 [`Dict`](@ref) 不同，`WeakKeyDict` 在插入时不会转换键，因为这将意味着键对象在插入之前没有被引用。

另请参见 [`WeakRef`](@ref)。
