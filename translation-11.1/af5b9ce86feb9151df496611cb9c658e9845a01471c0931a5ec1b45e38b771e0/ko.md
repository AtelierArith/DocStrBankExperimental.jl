```
clear!(syms, pids=workers(); mod=Main)
```

모듈에서 전역 바인딩을 `nothing`으로 초기화하여 지웁니다. `syms`는 [`Symbol`](@ref) 유형이거나 `Symbol`의 컬렉션이어야 합니다. `pids`와 `mod`는 전역 변수를 재초기화할 프로세스와 모듈을 식별합니다. `mod` 아래에 정의된 이름만 지워집니다.

전역 상수를 지우려고 할 경우 예외가 발생합니다.
