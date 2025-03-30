```
IOBuffer(string::String)
```

주어진 문자열에 기반한 읽기 전용 `IOBuffer`를 생성합니다.

# 예제

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
