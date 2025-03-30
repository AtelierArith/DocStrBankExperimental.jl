```
splitext(path::AbstractString) -> (String, String)
```

경로의 마지막 구성 요소에 하나 이상의 점이 포함되어 있으면, 경로를 마지막 점 이전의 모든 것과 점을 포함한 이후의 모든 것으로 나눕니다. 그렇지 않으면, 인수를 수정하지 않은 튜플과 빈 문자열을 반환합니다. "splitext"는 "split extension"의 약자입니다.

# 예시

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
