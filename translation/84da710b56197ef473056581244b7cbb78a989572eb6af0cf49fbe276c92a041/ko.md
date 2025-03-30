```
LinRange{T,L}
```

`start`와 `stop` 사이에 `len` 개의 선형으로 간격이 있는 요소를 가진 범위입니다. 간격의 크기는 `len`에 의해 제어되며, 이는 `Integer` 여야 합니다.

# 예제

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

[`range`](@ref)를 사용하는 것과 비교할 때, `LinRange`를 직접 구성하는 것이 오버헤드가 적지만 부동 소수점 오류를 수정하려고 하지는 않습니다:

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

로그arithmically 간격이 있는 점에 대해서는 [`Logrange`](@ref Base.LogRange)도 참조하세요.
