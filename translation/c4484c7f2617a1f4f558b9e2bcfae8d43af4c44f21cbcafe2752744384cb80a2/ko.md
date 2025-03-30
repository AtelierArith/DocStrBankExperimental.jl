```
truncate(file, n)
```

파일 또는 버퍼를 첫 번째 인수로 주어진 대로 정확히 `n` 바이트로 크기를 조정하며, 파일 또는 버퍼가 커질 경우 이전에 할당되지 않은 공간을 '\0'으로 채웁니다.

# 예제

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.")
35

julia> truncate(io, 15)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=15, maxsize=Inf, ptr=16, mark=-1)

julia> String(take!(io))
"JuliaLang is a "

julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.");

julia> truncate(io, 40);

julia> String(take!(io))
"JuliaLang is a GitHub organization.\0\0\0\0\0"
```
