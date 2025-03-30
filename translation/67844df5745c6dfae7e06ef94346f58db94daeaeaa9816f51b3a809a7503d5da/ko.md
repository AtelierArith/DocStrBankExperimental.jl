```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

주어진 제네릭 함수와 타입 시그니처에 맞는 메서드를 실행하기 위해 생성된 LLVM 비트코드를 `io`에 출력합니다.

`optimize` 키워드가 설정되지 않은 경우, 코드는 LLVM 최적화 이전에 표시됩니다. 모든 메타데이터와 dbg.* 호출은 출력된 비트코드에서 제거됩니다. 전체 IR을 보려면 `raw` 키워드를 true로 설정하십시오. 함수(선언 포함)를 캡슐화하는 전체 모듈을 덤프하려면 `dump_module` 키워드를 true로 설정하십시오. 키워드 인수 `debuginfo`는 코드 주석의 상세 수준을 지정하기 위해 source(기본값) 또는 none 중 하나일 수 있습니다.

참고: [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref).
