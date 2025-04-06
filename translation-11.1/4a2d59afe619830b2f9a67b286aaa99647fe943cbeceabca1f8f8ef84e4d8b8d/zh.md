```
mapfoldr(f, op, itr; [init])
```

类似于 [`mapreduce`](@ref)，但保证右结合性，如同 [`foldr`](@ref)。如果提供，关键字参数 `init` 将被使用一次。在一般情况下，处理空集合时需要提供 `init`。
