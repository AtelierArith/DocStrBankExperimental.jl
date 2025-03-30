```
styled(content::AbstractString) -> AnnotatedString
```

스타일이 적용된 문자열을 생성합니다. 문자열 내에서 `{<specs>:<content>}` 구조는 `<content>`에 대해 쉼표로 구분된 사양 목록 `<specs>`에 따라 형식을 적용합니다. 각 사양은 얼굴 이름, 인라인 얼굴 사양 또는 `key=value` 쌍의 형태를 취할 수 있습니다. 값이 `,=:{}` 중 하나의 문자를 포함하는 경우 `{...}`로 감싸야 합니다.

이는 [`@styled_str`](@ref) 매크로의 기능적 동등물로, 단지 보간 기능이 없습니다.
