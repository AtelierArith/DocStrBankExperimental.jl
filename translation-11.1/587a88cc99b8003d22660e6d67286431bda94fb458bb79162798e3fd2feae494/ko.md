```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

주어진 제네릭 함수 및 타입 서명에 맞는 메서드를 실행하기 위해 생성된 네이티브 어셈블리 명령어를 `io`에 출력합니다.

  * `syntax`를 `:intel` (기본값)으로 설정하여 인텔 구문을 사용하거나 `:att`로 설정하여 AT&T 구문을 사용하여 어셈블리 구문을 설정합니다.
  * `debuginfo`를 `:source` (기본값) 또는 `:none`으로 설정하여 코드 주석의 상세도를 지정합니다.
  * `binary`가 `true`인 경우, 각 명령어 앞에 약어 주소가 붙은 이진 기계 코드를 출력합니다.
  * `dump_module`이 `false`인 경우, rodata 또는 지시문과 같은 메타데이터를 출력하지 않습니다.
  * `raw`가 `false`인 경우, 흥미롭지 않은 명령어(예: safepoint 함수 프로롤로그)는 생략됩니다.

참고: [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref).
