```
objectid(x) -> UInt
```

객체의 정체성에 기반하여 `x`에 대한 해시 값을 가져옵니다.

`x === y`이면 `objectid(x) == objectid(y)`이고, 일반적으로 `x !== y`일 때 `objectid(x) != objectid(y)`입니다.

또한 [`hash`](@ref), [`IdDict`](@ref)를 참조하세요.
