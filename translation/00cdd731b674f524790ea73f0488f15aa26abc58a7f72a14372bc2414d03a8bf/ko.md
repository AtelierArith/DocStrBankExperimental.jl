`BroadcastStyle`는 브로드캐스팅 하에서 객체의 동작을 결정하는 데 사용되는 추상 타입 및 특성 함수입니다. `BroadcastStyle(typeof(x))`는 `x`와 관련된 스타일을 반환합니다. 타입의 브로드캐스팅 동작을 사용자 정의하려면, 타입/메서드 쌍을 정의하여 스타일을 선언할 수 있습니다.

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

그런 다음 `Broadcasted{MyContainerStyle}`에서 작동하는 메서드(최소한 [`similar`](@ref))를 작성합니다. 또한 활용할 수 있는 여러 미리 정의된 `BroadcastStyle`의 하위 타입이 있습니다. 더 많은 정보는 [Interfaces chapter](@ref man-interfaces-broadcasting)를 참조하세요.
