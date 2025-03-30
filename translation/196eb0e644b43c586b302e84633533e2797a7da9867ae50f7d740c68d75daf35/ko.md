```
isbitstype(T)
```

타입 `T`가 "일반 데이터" 타입인 경우 `true`를 반환합니다. 이는 불변이며 다른 값에 대한 참조가 없고, 오직 `primitive` 타입과 다른 `isbitstype` 타입만 포함된다는 의미입니다. 전형적인 예로는 [`UInt8`](@ref), [`Float64`](@ref), 및 [`Complex{Float64}`](@ref)와 같은 숫자 타입이 있습니다. 이 타입 카테고리는 타입 매개변수로 유효하며, [`isdefined`](@ref) / [`isassigned`](@ref) 상태를 추적하지 않을 수 있고, C와 호환되는 정의된 레이아웃을 가지고 있기 때문에 중요합니다. 만약 `T`가 타입이 아니라면 `false`를 반환합니다.

또한 [`isbits`](@ref), [`isprimitivetype`](@ref), [`ismutable`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
