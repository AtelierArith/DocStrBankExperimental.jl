```
skipmissing(itr)
```

`itr`의 요소를 반복하면서 [`missing`](@ref) 값을 건너뛰는 반복기를 반환합니다. 반환된 객체는 `itr`의 인덱스를 사용하여 인덱싱할 수 있으며, 후자가 인덱스 가능할 경우에 해당합니다. 누락된 값에 해당하는 인덱스는 유효하지 않으며, [`keys`](@ref) 및 [`eachindex`](@ref)에 의해 건너뛰어지고, 이를 사용하려고 할 때 `MissingException`이 발생합니다.

[`collect`](@ref)를 사용하여 `itr`에서 비-`missing` 값을 포함하는 `Array`를 얻을 수 있습니다. `itr`이 다차원 배열인 경우에도 결과는 항상 `Vector`가 되며, 입력의 차원을 유지하면서 누락된 값을 제거하는 것은 불가능합니다.

또한 [`coalesce`](@ref), [`ismissing`](@ref), [`something`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
ERROR: MissingException: the value at index (2,) is missing
[...]

julia> argmax(x)
3

julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
2-element Vector{Int64}:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
2-element Vector{Int64}:
 1
 2
```
