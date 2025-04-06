```
Printf.Format(format_str)
```

값을 포맷하는 데 사용할 수 있는 C printf 호환 포맷 객체를 생성합니다.

입력 `format_str`은 유효한 포맷 지정자 문자와 수정자를 포함할 수 있습니다.

`Format` 객체는 `Printf.format(f::Format, args...)`에 전달되어 포맷된 문자열을 생성하거나, `Printf.format(io::IO, f::Format, args...)`에 전달되어 포맷된 문자열을 직접 `io`에 출력할 수 있습니다.

편의를 위해, `Printf.format"..."` 문자열 매크로 형식을 사용하여 매크로 확장 시간에 `Printf.Format` 객체를 생성할 수 있습니다.

!!! compat "Julia 1.6"
    `Printf.Format`은 Julia 1.6 이상이 필요합니다.

