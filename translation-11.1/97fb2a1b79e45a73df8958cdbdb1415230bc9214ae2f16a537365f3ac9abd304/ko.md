```
readeach(io::IO, T)
```

[`read(io, T)`](@ref)를 생성하는 반복 가능한 객체를 반환합니다.

또한 [`skipchars`](@ref), [`eachline`](@ref), [`readuntil`](@ref)를 참조하세요.

!!! compat "Julia 1.6"
    `readeach`는 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for c in readeach(io, Char)
           c == '\n' && break
           print(c)
       end
JuliaLang is a GitHub organization.
```
