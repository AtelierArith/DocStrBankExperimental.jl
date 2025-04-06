```
codeunits(s::AbstractString)
```

문자열의 코드 유닛을 포함하는 벡터와 유사한 객체를 얻습니다. 기본적으로 `CodeUnits` 래퍼를 반환하지만, 필요에 따라 새로운 문자열 유형에 대해 `codeunits`를 선택적으로 정의할 수 있습니다.

# 예제

```jldoctest
julia> codeunits("Juλia")
6-element Base.CodeUnits{UInt8, String}:
 0x4a
 0x75
 0xce
 0xbb
 0x69
 0x61
```
