```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

다차원 직사각형 범위의 정수 인덱스를 포함하는 영역 `R`을 정의합니다. 이는 반복(iteration) 맥락에서 가장 일반적으로 사용되며, `for I in R ... end`는 중첩 루프에 해당하는 [`CartesianIndex`](@ref) 인덱스 `I`를 반환합니다.

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

따라서 이는 임의의 차원에서 작동하는 알고리즘을 작성하는 데 유용할 수 있습니다.

```
CartesianIndices(A::AbstractArray) -> R
```

편의상, 배열에서 `CartesianIndices`를 구성하면 해당 인덱스의 범위를 만듭니다.

!!! compat "Julia 1.6"
    단계 범위 방법 `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))`는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> foreach(println, CartesianIndices((2, 2, 2)))
CartesianIndex(1, 1, 1)
CartesianIndex(2, 1, 1)
CartesianIndex(1, 2, 1)
CartesianIndex(2, 2, 1)
CartesianIndex(1, 1, 2)
CartesianIndex(2, 1, 2)
CartesianIndex(1, 2, 2)
CartesianIndex(2, 2, 2)

julia> CartesianIndices(fill(1, (2,3)))
CartesianIndices((2, 3))
```

## 선형 인덱스와 카르테시안 인덱스 간의 변환

선형 인덱스를 카르테시안 인덱스로 변환하는 것은 `CartesianIndices`가 `AbstractArray`이며 선형으로 인덱싱할 수 있다는 사실을 활용합니다:

```jldoctest
julia> cartesian = CartesianIndices((1:3, 1:2))
CartesianIndices((1:3, 1:2))

julia> cartesian[4]
CartesianIndex(1, 2)

julia> cartesian = CartesianIndices((1:2:5, 1:2))
CartesianIndices((1:2:5, 1:2))

julia> cartesian[2, 2]
CartesianIndex(3, 2)
```

## 브로드캐스팅

`CartesianIndices`는 `CartesianIndex`와의 브로드캐스팅 산술(+ 및 -)을 지원합니다.

!!! compat "Julia 1.1"
    CartesianIndices의 브로드캐스팅은 최소한 Julia 1.1이 필요합니다.


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

카르테시안에서 선형 인덱스로의 변환에 대해서는 [`LinearIndices`](@ref)를 참조하십시오. ```
