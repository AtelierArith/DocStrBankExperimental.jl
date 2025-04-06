```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

`str`의 `range` (또는 전체 문자열)에 레이블이 있는 값(`label` => `value`)으로 주석을 추가합니다. 기존의 `label` 주석을 제거하려면 `nothing` 값을 사용하십시오.

`str`에 주석이 적용되는 순서는 [`AnnotatedString`](@ref)에서 설명한 대로 의미가 있습니다.
