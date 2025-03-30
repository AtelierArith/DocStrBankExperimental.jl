```
randstring([rng=default_rng()], [chars], [len=8])
```

创建一个长度为 `len` 的随机字符串，由 `chars` 中的字符组成，默认字符集为大小写字母和数字 0-9。可选的 `rng` 参数指定一个随机数生成器，参见 [Random Numbers](@ref)。

# 示例

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! 注意     `chars` 可以是任何字符集合，类型为 `Char` 或 `UInt8`（更高效），前提是 [`rand`](@ref) 可以从中随机选择字符。
