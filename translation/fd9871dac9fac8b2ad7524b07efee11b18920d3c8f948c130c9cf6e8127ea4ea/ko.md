```
Base64DecodePipe(istream)
```

읽기 전용 I/O 스트림을 반환하며, `istream`에서 읽은 base64 인코딩된 데이터를 디코딩합니다.

# 예제

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
