```
sizeof(str::AbstractString)
```

문자열 `str`의 크기(바이트 단위). `str`의 코드 유닛 수에 `str`의 코드 유닛 하나의 크기(바이트 단위)를 곱한 값과 같습니다.

# 예제

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
