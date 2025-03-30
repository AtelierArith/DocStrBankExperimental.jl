```
@enum EnumName[::BaseType] value1[=x] value2[=y]
```

`EnumName`이라는 이름의 `Enum{BaseType}` 하위 유형을 생성하고, 선택적으로 할당된 값 `x`와 `y`를 가진 `value1` 및 `value2`의 열거형 멤버 값을 정의합니다. `EnumName`은 다른 유형과 마찬가지로 사용될 수 있으며, 열거형 멤버 값은 일반 값으로 사용될 수 있습니다. 예를 들어:

# 예시

```jldoctest fruitenum
julia> @enum Fruit apple=1 orange=2 kiwi=3

julia> f(x::Fruit) = "I'm a Fruit with value: $(Int(x))"
f (generic function with 1 method)

julia> f(apple)
"I'm a Fruit with value: 1"

julia> Fruit(1)
apple::Fruit = 1
```

값은 `begin` 블록 안에서도 지정할 수 있습니다. 예를 들어:

```julia
@enum EnumName begin
    value1
    value2
end
```

기본값은 [`Int32`](@ref)인 `BaseType`은 `Integer`의 원시 하위 유형이어야 합니다. 멤버 값은 열거형 유형과 `BaseType` 간에 변환될 수 있습니다. `read`와 `write`는 이러한 변환을 자동으로 수행합니다. 비기본 `BaseType`으로 열거형이 생성된 경우, `Integer(value1)`은 `BaseType` 유형의 정수 `value1`을 반환합니다.

열거형의 모든 인스턴스를 나열하려면 `instances`를 사용합니다. 예를 들어:

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```

열거형 인스턴스에서 기호를 구성하는 것도 가능합니다:

```jldoctest fruitenum
julia> Symbol(apple)
:apple
```
