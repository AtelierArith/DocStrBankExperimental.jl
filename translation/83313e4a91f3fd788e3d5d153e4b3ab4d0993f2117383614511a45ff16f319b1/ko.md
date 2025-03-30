```
println([io::IO], xs...)
```

`xs`를 `io`에 출력한 후 줄 바꿈을 합니다 ( [`print`](@ref) 사용). `io`가 제공되지 않으면 기본 출력 스트림 [`stdout`](@ref)에 출력합니다.

색상 등을 추가하려면 [`printstyled`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> println("Hello, world")
Hello, world

julia> io = IOBuffer();

julia> println(io, "Hello", ',', " world.")

julia> String(take!(io))
"Hello, world.\n"
```
