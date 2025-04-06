```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

메모리 내 I/O 스트림을 생성하며, 선택적으로 기존 배열에서 작동할 수 있습니다.

선택적 키워드 인수를 받을 수 있습니다:

  * `read`, `write`, `append`: 버퍼에 대한 작업을 제한합니다; 자세한 내용은 `open`을 참조하십시오.
  * `truncate`: 버퍼 크기를 0 길이로 잘라냅니다.
  * `maxsize`: 버퍼가 성장할 수 없는 크기를 지정합니다.
  * `sizehint`: 버퍼의 용량을 제안합니다 (`data`는 `sizehint!(data, size)`를 구현해야 합니다).

`data`가 주어지지 않으면, 버퍼는 기본적으로 읽기 및 쓰기가 가능합니다.

# 예제

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> io = IOBuffer(b"JuliaLang is a GitHub organization.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang is a GitHub organization."

julia> write(io, "This isn't writable.")
ERROR: ArgumentError: ensureroom failed, IOBuffer is not writeable

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang is a GitHub organization.")
34

julia> String(take!(io))
"JuliaLang is a GitHub organization"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
