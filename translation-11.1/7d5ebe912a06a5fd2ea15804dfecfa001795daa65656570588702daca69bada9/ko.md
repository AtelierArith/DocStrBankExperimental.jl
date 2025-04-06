```
__precompile__(isprecompilable::Bool)
```

이 함수를 호출하는 파일이 사전 컴파일 가능한지 여부를 지정하며, 기본값은 `true`입니다. 모듈이나 파일이 *안전하게* 사전 컴파일할 수 없는 경우, Julia가 이를 사전 컴파일하려고 할 때 오류를 발생시키기 위해 `__precompile__(false)`를 호출해야 합니다.
