```
fieldname(x::DataType, i::Integer)
```

`DataType`의 필드 `i`의 이름을 가져옵니다.

# 예제

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
