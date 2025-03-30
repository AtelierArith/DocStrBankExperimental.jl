```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

전통적인 C 및 유니코드 이스케이프 시퀀스의 일반적인 언이스케이프. 첫 번째 형식은 이스케이프된 문자열을 반환하고, 두 번째는 결과를 `io`에 출력합니다. 인수 `keep`는 (역슬래시와 함께) 그대로 유지할 문자의 컬렉션을 지정합니다.

다음 이스케이프 시퀀스가 인식됩니다:

  * 이스케이프된 역슬래시 (`\\`)
  * 이스케이프된 큰따옴표 (`\"`)
  * 표준 C 이스케이프 시퀀스 (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * 유니코드 BMP 코드 포인트 (`\u` 뒤에 1-4개의 16진수 숫자)
  * 모든 유니코드 코드 포인트 (`\U` 뒤에 1-8개의 16진수 숫자; 최대 값 = 0010ffff)
  * 16진수 바이트 (`\x` 뒤에 1-2개의 16진수 숫자)
  * 8진수 바이트 (`\` 뒤에 1-3개의 8진수 숫자)

또한 [`escape_string`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> unescape_string("aaa\\nbbb") # C 이스케이프 시퀀스
"aaa\nbbb"

julia> unescape_string("\\u03c0") # 유니코드
"π"

julia> unescape_string("\\101") # 8진수
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # `keep` 인수 사용
"aaa \\g \n"
```
