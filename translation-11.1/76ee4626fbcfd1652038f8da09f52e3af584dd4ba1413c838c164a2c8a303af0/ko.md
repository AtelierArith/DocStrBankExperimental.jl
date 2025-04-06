```
mmap(io, BitArray, [dims, offset])
```

메모리 매핑을 사용하여 파일에 연결된 [`BitArray`](@ref)를 생성합니다. 이는 동일한 목적을 가지고 있으며, 동일한 방식으로 작동하고, [`mmap`](@ref mmap)과 동일한 인수를 가집니다. 그러나 바이트 표현은 다릅니다.

# 예제

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

이 코드는 스트림 `io`와 연결된 25x30000 `BitArray`를 생성합니다.
