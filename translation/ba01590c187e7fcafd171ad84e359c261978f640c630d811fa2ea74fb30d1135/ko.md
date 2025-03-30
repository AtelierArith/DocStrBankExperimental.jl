```
fld1(x, y)
```

바닥 나눗셈, `mod1(x,y)`와 일치하는 값을 반환합니다.

또한 [`mod1`](@ref), [`fldmod1`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> x = 15; y = 4;

julia> fld1(x, y)
4

julia> x == fld(x, y) * y + mod(x, y)
true

julia> x == (fld1(x, y) - 1) * y + mod1(x, y)
true
```
