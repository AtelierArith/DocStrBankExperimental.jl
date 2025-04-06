```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

전역 변수 또는 객체 필드가 정의되어 있는지 테스트합니다. 인수는 모듈과 기호 또는 복합 객체와 필드 이름(기호로) 또는 인덱스가 될 수 있습니다. 선택적으로, 작업에 대한 순서를 정의할 수 있습니다. 필드가 `@atomic`으로 선언된 경우, 해당 위치에 대한 저장소와 호환되도록 사양이 강력히 권장됩니다. 그렇지 않으면 `@atomic`으로 선언되지 않은 경우, 이 매개변수는 지정된 경우 `:not_atomic`이어야 합니다.

배열 요소가 정의되어 있는지 테스트하려면 [`isassigned`](@ref)를 대신 사용하십시오.

또한 [`@isdefined`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
