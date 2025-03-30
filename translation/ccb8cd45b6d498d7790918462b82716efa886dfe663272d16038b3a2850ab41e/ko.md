```
names(x::Module; all::Bool = false, imported::Bool = false)
```

`Module`의 공개 이름의 벡터를 가져옵니다. 단, 더 이상 사용되지 않는 이름은 제외됩니다. `all`이 true인 경우, 목록에는 모듈에 정의된 비공식 이름, 더 이상 사용되지 않는 이름 및 컴파일러가 생성한 이름도 포함됩니다. `imported`가 true인 경우, 다른 모듈에서 명시적으로 가져온 이름도 포함됩니다. 이름은 정렬된 순서로 반환됩니다.

특별한 경우로, `Main`에 정의된 모든 이름은 "공식"으로 간주됩니다. 왜냐하면 `Main`의 이름을 공개로 명시적으로 표시하는 것은 관례에 맞지 않기 때문입니다.

!!! note
    `sym ∈ names(SomeModule)`는 `isdefined(SomeModule, sym)`을 *의미하지* 않습니다. `names`는 모듈에 정의되지 않았더라도 `public` 또는 `export`로 표시된 기호를 반환합니다.


참고: [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
