```
@code_llvm
```

함수 또는 매크로 호출에 대한 인수를 평가하고, 그들의 유형을 결정한 다음, 결과 표현식에 대해 [`code_llvm`](@ref)를 호출합니다. 선택적 키워드 인수 `raw`, `dump_module`, `debuginfo`, `optimize`를 함수 호출 전에 다음과 같이 넣어 설정할 수 있습니다:

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize`는 인라인과 같은 추가 최적화가 적용되는지를 제어합니다. `raw`는 모든 메타데이터와 dbg.* 호출을 표시합니다. `debuginfo`는 코드 주석의 상세 수준을 지정하기 위해 `:source`(기본값) 또는 `:none` 중 하나일 수 있습니다. `dump_module`은 함수를 캡슐화하는 전체 모듈을 출력합니다.

참고: [`code_llvm`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_native`](@ref).
