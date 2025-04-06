```
take!(b::IOBuffer)
```

`IOBuffer`의 내용을 배열로 가져옵니다. 이후 `IOBuffer`는 초기 상태로 재설정됩니다.

# 예제

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."
```
