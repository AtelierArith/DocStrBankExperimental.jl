```
FILE(::Ptr)
FILE(::IO)
```

libc `FILE*`는 열린 파일을 나타냅니다.

`Ptr{FILE}` 인수로 [`ccall`](@ref)에 전달할 수 있으며, [`seek`](@ref), [`position`](@ref) 및 [`close`](@ref)도 지원합니다.

`FILE`은 일반 `IO` 객체에서 생성할 수 있으며, 이 객체는 열린 파일이어야 합니다. 이후에는 닫아야 합니다.

# 예제

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # libc의 `puts(char*, FILE*)`를 사용하여 임시 파일에 쓰기
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # 파일을 다시 읽기
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
