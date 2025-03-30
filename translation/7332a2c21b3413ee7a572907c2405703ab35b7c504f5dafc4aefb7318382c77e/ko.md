```
methodswith(typ[, module or function]; supertypes::Bool=false])
```

`typ` 유형의 인수를 가진 메서드의 배열을 반환합니다.

선택적 두 번째 인수는 특정 모듈이나 함수로 검색을 제한합니다(기본값은 모든 최상위 모듈).

`supertypes` 키워드가 `true`인 경우, `Any` 유형을 제외하고 `typ`의 부모 유형을 가진 인수도 반환합니다.

또한: [`methods`](@ref).
