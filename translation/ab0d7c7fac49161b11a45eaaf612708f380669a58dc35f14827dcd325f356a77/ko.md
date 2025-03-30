```
summary(io::IO, x)
str = summary(x)
```

값에 대한 간단한 설명을 제공하는 스트림 `io`에 인쇄하거나 문자열 `str`을 반환합니다. 기본적으로 `string(typeof(x))`를 반환합니다. 예: [`Int64`](@ref).

배열의 경우 크기 및 유형 정보의 문자열을 반환합니다. 예: `10-element Array{Int64,1}`.

# 예제

```jldoctest
julia> summary(1)
"Int64"

julia> summary(zeros(2))
"2-element Vector{Float64}"
```
