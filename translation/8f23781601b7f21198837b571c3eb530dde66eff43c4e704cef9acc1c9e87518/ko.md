```
fieldnames(x::DataType)
```

`DataType`의 필드 이름을 포함하는 튜플을 가져옵니다.

또한 [`propertynames`](@ref), [`hasfield`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
