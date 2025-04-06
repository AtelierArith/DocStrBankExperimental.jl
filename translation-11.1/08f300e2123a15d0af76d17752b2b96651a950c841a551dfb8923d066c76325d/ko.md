```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

주어진 문자열 객체의 코드 유닛 유형을 반환합니다. ASCII, Latin-1 또는 UTF-8 인코딩 문자열의 경우 `UInt8`이 됩니다. UCS-2 및 UTF-16의 경우 `UInt16`이 되고, UTF-32의 경우 `UInt32`가 됩니다. 코드 유닛 유형은 이 세 가지 유형으로 제한될 필요는 없지만, 이들 유닛 중 하나를 사용하지 않는 널리 사용되는 문자열 인코딩을 생각하기는 어렵습니다. `codeunit(s)`는 `s`가 비어 있지 않은 문자열일 때 `typeof(codeunit(s,1))`와 동일합니다.

자세한 내용은 [`ncodeunits`](@ref)를 참조하세요.
