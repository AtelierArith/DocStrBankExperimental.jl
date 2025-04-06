```
enumerate(iter)
```

一个迭代器，生成 `(i, x)`，其中 `i` 是从 1 开始的计数器，`x` 是来自给定迭代器的第 `i` 个值。当你不仅需要迭代的值 `x`，而且还需要到目前为止的迭代次数时，这非常有用。

请注意，`i` 可能不适用于索引 `iter`，或者可能索引到不同的元素。如果 `iter` 的索引不是从 1 开始的，或者对于字符串、字典等情况，这种情况可能会发生。如果你想确保 `i` 是一个索引，请参见 `pairs(IndexLinear(), iter)` 方法。

# 示例

```jldoctest
julia> a = ["a", "b", "c"];

julia> for (index, value) in enumerate(a)
           println("$index $value")
       end
1 a
2 b
3 c

julia> str = "naïve";

julia> for (i, val) in enumerate(str)
           print("i = ", i, ", val = ", val, ", ")
           try @show(str[i]) catch e println(e) end
       end
i = 1, val = n, str[i] = 'n'
i = 2, val = a, str[i] = 'a'
i = 3, val = ï, str[i] = 'ï'
i = 4, val = v, StringIndexError("naïve", 4)
i = 5, val = e, str[i] = 'v'
```
