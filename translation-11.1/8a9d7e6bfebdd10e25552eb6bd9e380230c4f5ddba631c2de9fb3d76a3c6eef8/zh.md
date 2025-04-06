```
反序列化(stream)
```

读取由 [`serialize`](@ref) 写入的值。`deserialize` 假设从 `stream` 读取的二进制数据是正确的，并且已由兼容的 [`serialize`](@ref) 实现序列化。`deserialize` 旨在简化和提高性能，因此不验证读取的数据。格式错误的数据可能导致进程终止。调用者必须确保从 `stream` 读取的数据的完整性和正确性。
