```
@code_typed
```

함수 또는 매크로 호출에 대한 인수를 평가하고, 그들의 유형을 결정한 다음, 결과 표현식에 대해 [`code_typed`](@ref)를 호출합니다. 선택적 인수 `optimize`를 사용하여

```
@code_typed optimize=true foo(x)
```

인라인과 같은 추가 최적화가 적용되는지 여부를 제어할 수 있습니다.

또한 참조: [`code_typed`](@ref), [`@code_warntype`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref), [`@code_native`](@ref).
