```
typeintersect(T::Type, S::Type)
```

`T`와 `S`의 교차점을 포함하는 타입을 계산합니다. 일반적으로 이는 가장 작은 그러한 타입이거나 그에 가까운 타입이 될 것입니다.

정확한 동작이 보장되는 특별한 경우: `T <: S`일 때, `typeintersect(S, T) == T == typeintersect(T, S)`입니다.
