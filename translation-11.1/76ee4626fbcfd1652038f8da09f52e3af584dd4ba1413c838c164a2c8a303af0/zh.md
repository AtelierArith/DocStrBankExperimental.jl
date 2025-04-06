```
mmap(io, BitArray, [dims, offset])
```

创建一个 [`BitArray`](@ref)，其值与文件相关联，使用内存映射；它具有相同的目的，以相同的方式工作，并具有与 [`mmap`](@ref mmap) 相同的参数，但字节表示不同。

# 示例

```jldoctest
julia> using Mmap

julia> io = open("mmap.bin", "w+");

julia> B = mmap(io, BitArray, (25,30000));

julia> B[3, 4000] = true;

julia> Mmap.sync!(B);

julia> close(io);

julia> io = open("mmap.bin", "r+");

julia> C = mmap(io, BitArray, (25,30000));

julia> C[3, 4000]
true

julia> C[2, 4000]
false

julia> close(io)

julia> rm("mmap.bin")
```

这创建了一个 25x30000 的 `BitArray`，与流 `io` 关联的文件相关联。
