```
codeunits(s::AbstractString)
```

获取一个包含字符串代码单元的类似向量的对象。默认情况下返回一个 `CodeUnits` 包装器，但如果需要，可以为新的字符串类型可选地定义 `codeunits`。

# 示例

```jldoctest
julia> codeunits("Juλia")
6-element Base.CodeUnits{UInt8, String}:
 0x4a
 0x75
 0xce
 0xbb
 0x69
 0x61
```
