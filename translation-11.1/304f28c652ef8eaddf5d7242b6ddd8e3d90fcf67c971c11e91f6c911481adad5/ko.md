```
@sprintf("%Fmt", args...)
```

문자열로 [`@printf`](@ref) 형식의 출력을 반환합니다.

# 예시

```jldoctest
julia> @sprintf "this is a %s %15.1f" "test" 34.567
"this is a test            34.6"
```
