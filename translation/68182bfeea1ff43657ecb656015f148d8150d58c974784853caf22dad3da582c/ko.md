```
Sampler(rng, x, repetition = Val(Inf))
```

`rng`에서 `x`의 무작위 값을 생성하는 데 사용할 수 있는 샘플러 객체를 반환합니다.

`sp = Sampler(rng, x, repetition)`일 때, `rand(rng, sp)`는 무작위 값을 추출하는 데 사용되며, 그에 따라 정의되어야 합니다.

`repetition`은 `Val(1)` 또는 `Val(Inf)`일 수 있으며, 해당하는 경우 사전 계산의 양을 결정하는 제안으로 사용되어야 합니다.

[`Random.SamplerType`](@ref) 및 [`Random.SamplerTrivial`](@ref)는 각각 *타입* 및 *값*에 대한 기본 대체입니다. [`Random.SamplerSimple`](@ref)는 이 목적만을 위해 추가 타입을 정의하지 않고도 사전 계산된 값을 저장하는 데 사용할 수 있습니다.
