```
mod(x, y)
rem(x, y, RoundDown)
```

`x`를 `y`로 나눈 나머지, 또는 동등하게 `y`로 나눈 후 내림한 나눗셈에 대한 `x`의 나머지, 즉 중간 반올림 없이 계산할 경우 `x - y*fld(x,y)`입니다.

결과는 `y`와 같은 부호를 가지며, 크기는 `abs(y)`보다 작습니다(일부 예외가 있으니 아래의 주석을 참조하세요).

!!! note
    부동 소수점 값과 함께 사용될 때, 정확한 결과는 해당 타입으로 표현할 수 없을 수 있으며, 따라서 반올림 오류가 발생할 수 있습니다. 특히, 정확한 결과가 `y`에 매우 가까운 경우, `y`로 반올림될 수 있습니다.


참고: [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
