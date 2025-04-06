```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

구문 `@atomic op(x.f, v)` (및 그에 해당하는 `@atomic x.f op v`)는 `modifyproperty!(x, :f, op, v, :sequentially_consistent)`를 반환하며, 여기서 첫 번째 인자는 `getproperty` 표현식이어야 하고 원자적으로 수정됩니다.

`op(getproperty(x, f), v)`의 호출은 기본적으로 객체 `x`의 필드 `f`에 저장할 수 있는 값을 반환해야 합니다. 특히, [`setproperty!`](@ref Base.setproperty!)의 기본 동작과 달리, `convert` 함수는 자동으로 호출되지 않습니다.

또한 [`modifyfield!`](@ref Core.modifyfield!) 및 [`setproperty!`](@ref Base.setproperty!)를 참조하십시오.
