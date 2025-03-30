```
struct SimpleColor
```

색상의 기본 표현으로, 문자열 스타일링 목적으로 사용됩니다. 이름이 지정된 색상(`:red`와 같은) 또는 8비트 깊이의 `r`, `g`, `b` 색상을 지정하는 NamedTuple인 `RGBTuple`을 포함할 수 있습니다.

# 생성자

```julia
SimpleColor(name::Symbol)  # 예: :red
SimpleColor(rgb::RGBTuple) # 예: (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # 예: 0x123456
```

또한 `tryparse(SimpleColor, rgb::String)`를 참조하십시오.
