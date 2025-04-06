```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

주어진 정수 유형의 구성 요소를 가진 [`Rational`](@ref) 숫자로 부동 소수점 숫자 `x`를 근사화합니다. 결과는 `tol`보다 `x`와 차이가 나지 않습니다.

# 예제

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
