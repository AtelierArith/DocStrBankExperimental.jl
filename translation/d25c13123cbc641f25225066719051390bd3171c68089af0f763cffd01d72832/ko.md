```
@goto name
```

`@goto name`는 [`@label name`](@ref) 위치의 문으로 무조건 점프합니다.

`@label`과 `@goto`는 서로 다른 최상위 문으로 점프를 생성할 수 없습니다. 시도할 경우 오류가 발생합니다. 여전히 `@goto`를 사용하려면 `@label`과 `@goto`를 블록으로 감싸야 합니다.
