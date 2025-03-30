```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

구성 요소 `value`에서 이름이나 위치로 필드를 추출합니다. 선택적으로, 작업을 위한 순서를 정의할 수 있습니다. 필드가 `@atomic`으로 선언된 경우, 해당 위치에 대한 저장소와 호환되도록 사양을 강력히 권장합니다. 그렇지 않으면 `@atomic`으로 선언되지 않은 경우, 지정된 경우 이 매개변수는 `:not_atomic`이어야 합니다. 또한 [`getproperty`](@ref Base.getproperty) 및 [`fieldnames`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
