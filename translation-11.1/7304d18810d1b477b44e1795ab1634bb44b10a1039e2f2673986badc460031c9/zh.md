```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

创建一个类似于 `IO` 的对象，用于创建未与文件绑定的零初始化的内存映射，供 [`mmap`](@ref mmap) 使用。`SharedArray` 用于创建共享内存数组。

# 示例

```jldoctest
julia> using Mmap

julia> anon = Mmap.Anonymous();

julia> isreadable(anon)
true

julia> iswritable(anon)
true

julia> isopen(anon)
true
```
