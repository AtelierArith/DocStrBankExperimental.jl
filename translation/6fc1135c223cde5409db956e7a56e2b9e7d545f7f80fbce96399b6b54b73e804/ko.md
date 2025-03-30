```
invoke(f, argtypes::Type, args...; kwargs...)
```

주어진 제네릭 함수 `f`에 대해 지정된 타입 `argtypes`와 지정된 인수 `args`에 대해 일치하는 메서드를 호출하고 키워드 인수 `kwargs`를 전달합니다. 인수 `args`는 `argtypes`에 지정된 타입과 일치해야 하며, 즉 자동으로 변환되지 않습니다. 이 메서드는 가장 구체적인 일치 메서드가 아닌 다른 메서드를 호출할 수 있게 해주며, 이는 더 구체적인 메서드의 구현의 일부로서 더 일반적인 정의의 동작이 명시적으로 필요할 때 유용합니다.

작성하지 않은 함수에 대해 `invoke`를 사용할 때는 주의해야 합니다. 주어진 `argtypes`에 대해 어떤 정의가 사용되는지는 구현 세부 사항이며, 함수가 특정 `argtypes`로 호출하는 것이 공개 API의 일부라고 명시적으로 언급하지 않는 한 그렇습니다. 예를 들어, 아래 예제에서 `f1`과 `f2` 간의 변화는 일반적인 (비 `invoke`) 호출로는 호출자에게 보이지 않기 때문에 일반적으로 호환 가능한 것으로 간주됩니다. 그러나 `invoke`를 사용하면 변화가 보입니다.

# 예제

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```
