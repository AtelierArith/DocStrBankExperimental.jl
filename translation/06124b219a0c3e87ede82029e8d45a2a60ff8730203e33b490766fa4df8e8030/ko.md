```
transcode(T, src)
```

문자열 데이터를 유니코드 인코딩 간에 변환합니다. `src`는 `String` 또는 UTF-XX 코드 유닛의 `Vector{UIntXX}`로, 여기서 `XX`는 8, 16 또는 32입니다. `T`는 반환 값의 인코딩을 나타냅니다: `String`은 (UTF-8 인코딩된) `String`을 반환하고, `UIntXX`는 UTF-`XX` 데이터의 `Vector{UIntXX}`를 반환합니다. (별칭 [`Cwchar_t`](@ref)도 외부 C 라이브러리에서 사용되는 `wchar_t*` 문자열을 변환하는 데 사용할 수 있는 정수형입니다.)

`transcode` 함수는 입력 데이터가 대상 인코딩에서 합리적으로 표현될 수 있는 한 성공합니다. 유효하지 않은 유니코드 데이터에 대해서도 UTF-XX 인코딩 간의 변환은 항상 성공합니다.

현재 UTF-8로의 변환만 지원됩니다.

# 예제

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
