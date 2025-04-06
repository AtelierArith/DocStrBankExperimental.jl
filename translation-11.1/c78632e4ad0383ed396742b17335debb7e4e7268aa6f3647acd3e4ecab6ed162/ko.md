```
read(io::IO, T)
```

`io`에서 타입 `T`의 단일 값을 읽습니다. 표준 이진 표현으로.

Julia는 엔디안 변환을 자동으로 수행하지 않습니다. 이 목적을 위해 [`ntoh`](@ref) 또는 [`ltoh`](@ref)를 사용하십시오.

```
read(io::IO, String)
```

`io`의 전체 내용을 `String`으로 읽습니다 (자세한 내용은 [`readchomp`](@ref) 참조).

# 예제

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (category Lu: Letter, uppercase)

julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, String)
"JuliaLang is a GitHub organization"
```
