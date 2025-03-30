```
Regex(pattern[, flags]) <: AbstractPattern
```

정규 표현식을 나타내는 타입입니다. `Regex` 객체는 [`match`](@ref)와 함께 문자열을 일치시키는 데 사용할 수 있습니다.

`Regex` 객체는 [`@r_str`](@ref) 문자열 매크로를 사용하여 생성할 수 있습니다. `pattern` 문자열을 보간해야 하는 경우 일반적으로 `Regex(pattern[, flags])` 생성자를 사용합니다. 플래그에 대한 자세한 내용은 문자열 매크로의 문서를 참조하십시오.

!!! note
    보간된 변수를 이스케이프하려면 `\Q`와 `\E`를 사용하십시오 (예: `Regex("\\Q$x\\E")`)

