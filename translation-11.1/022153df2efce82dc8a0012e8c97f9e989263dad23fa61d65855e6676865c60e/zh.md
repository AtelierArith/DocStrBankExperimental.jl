```
iscntrl(c::AbstractChar) -> Bool
```

测试一个字符是否是控制字符。控制字符是拉丁-1子集Unicode的非打印字符。

# 示例

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
