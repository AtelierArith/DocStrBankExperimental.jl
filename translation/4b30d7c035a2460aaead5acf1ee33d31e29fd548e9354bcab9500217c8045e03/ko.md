```
AbstractIrrational <: Real
```

정확한 무리수를 나타내는 숫자 유형으로, 다른 숫자 양과의 산술 연산에서 자동으로 올바른 정밀도로 반올림됩니다.

하위 유형 `MyIrrational <: AbstractIrrational`은 최소한 `==(::MyIrrational, ::MyIrrational)`, `hash(x::MyIrrational, h::UInt)`, 및 `convert(::Type{F}, x::MyIrrational) where {F <: Union{BigFloat,Float32,Float64}}`를 구현해야 합니다.

하위 유형이 때때로 유리수를 나타내는 데 사용되는 경우(예: 정수 `n`에 대해 `√n`을 나타내는 제곱근 유형은 `n`이 완전 제곱일 때 유리한 결과를 제공합니다), `isinteger`, `iszero`, `isone`, 및 `==`를 `Real` 값과 함께 구현해야 합니다(모두 `AbstractIrrational` 유형에 대해 기본적으로 `false`로 설정되므로), 그리고 [`hash`](@ref)를 해당하는 `Rational`과 같도록 정의해야 합니다.
