```
bytesavailable(io)
```

이 스트림 또는 버퍼에서 읽기가 차단되기 전에 읽을 수 있는 바이트 수를 반환합니다.

# 예제

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> bytesavailable(io)
34
```
