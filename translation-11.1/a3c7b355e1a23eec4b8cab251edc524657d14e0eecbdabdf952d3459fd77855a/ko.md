```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

경로 구성 요소를 전체 경로로 결합합니다. 일부 인수가 절대 경로이거나 (Windows에서) 드라이브 사양이 이전 경로의 조합에 대해 계산된 드라이브와 일치하지 않으면 이전 구성 요소가 삭제됩니다.

Windows에서는 각 드라이브에 대한 현재 디렉토리가 있으므로 `joinpath("c:", "foo")`는 드라이브 "c:"의 현재 디렉토리에 대한 상대 경로를 나타내므로 이는 "c:foo"와 같고 "c:\foo"와 같지 않습니다. 또한, `joinpath`는 이를 비절대 경로로 처리하고 드라이브 문자 대소문자를 무시하므로 `joinpath("C:\A","c:b") = "C:\A\b"`입니다.

# 예제

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
