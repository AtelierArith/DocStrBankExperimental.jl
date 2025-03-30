```
Base.compilecache(module::PkgId)
```

为一个模块及其所有依赖项创建一个预编译缓存文件。这可以用来减少包加载时间。缓存文件存储在 `DEPOT_PATH[1]/compiled` 中。有关重要说明，请参见 [Module initialization and precompilation](@ref)。
