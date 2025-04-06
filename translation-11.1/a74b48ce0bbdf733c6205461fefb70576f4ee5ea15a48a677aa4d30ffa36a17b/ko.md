```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

제공된 `args`에 printf 형식 객체 `f`를 적용하고 형식화된 문자열을 반환합니다(1번째 메서드) 또는 `io` 객체에 직접 인쇄합니다(2번째 메서드). C `printf` 지원에 대한 자세한 내용은 [`@printf`](@ref)를 참조하십시오.
