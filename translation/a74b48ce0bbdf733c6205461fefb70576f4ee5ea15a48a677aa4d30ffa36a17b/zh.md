```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

将提供的 `args` 应用到 printf 格式对象 `f` 并返回格式化的字符串（第一个方法），或直接打印到 `io` 对象（第二个方法）。有关 C `printf` 支持的更多细节，请参见 [`@printf`](@ref)。
