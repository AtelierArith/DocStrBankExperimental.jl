```
@code_native
```

함수 또는 매크로 호출에 대한 인수를 평가하고, 그들의 유형을 결정한 다음, 결과 표현식에 대해 [`code_native`](@ref)를 호출합니다.

선택적 키워드 인수 `syntax`, `debuginfo`, `binary` 또는 `dump_module` 중 하나를 함수 호출 전에 다음과 같이 설정할 수 있습니다:

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * 어셈블리 구문을 설정하려면 `syntax`를 Intel 구문에 대해 `:intel` (기본값)으로 또는 AT&T 구문에 대해 `:att`로 설정합니다.
  * 코드 주석의 자세한 정도를 지정하려면 `debuginfo`를 `:source` (기본값) 또는 `:none`으로 설정합니다.
  * `binary`가 `true`인 경우, 각 명령어에 대해 약어 주소가 앞에 붙은 이진 기계 코드를 인쇄합니다.
  * `dump_module`가 `false`인 경우, rodata 또는 지시문과 같은 메타데이터를 인쇄하지 않습니다.

또한 참조: [`code_native`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref).
