```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')
```

`io`를 끝까지 읽고 줄 수를 셉니다. 파일을 지정하려면 파일 이름을 첫 번째 인수로 전달합니다. `'\n'` 이외의 EOL 마커는 두 번째 인수로 전달하여 지원됩니다. `io`의 마지막 비어 있지 않은 줄은 EOL로 끝나지 않더라도 계산되며, 이는 [`eachline`](@ref) 및 [`readlines`](@ref)에서 반환된 길이와 일치합니다.

`String`의 줄 수를 세려면 `countlines(IOBuffer(str))`를 사용할 수 있습니다.

# 예제

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n");

julia> countlines(io)
1

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io)
1

julia> eof(io) # 줄 수를 세면 파일 포인터가 이동합니다.
true

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io, eol = '.')
1
```

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n")
36

julia> countlines("my_file.txt")
1

julia> countlines("my_file.txt", eol = 'n')
4

julia> rm("my_file.txt")

```
