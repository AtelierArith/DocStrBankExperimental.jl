```
real(T::Type)
```

타입 `T`의 값의 실수 부분을 나타내는 타입을 반환합니다. 예: `T == Complex{R}`인 경우 `R`을 반환합니다. `typeof(real(zero(T)))`와 동등합니다.

# 예시

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
