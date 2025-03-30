```
last(s::AbstractString, n::Integer)
```

문자열 `s`의 마지막 `n` 문자로 구성된 문자열을 가져옵니다.

# 예제

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
