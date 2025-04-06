```
isreadonly(io) -> Bool
```

스트림이 읽기 전용인지 여부를 결정합니다.

# 예제

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
