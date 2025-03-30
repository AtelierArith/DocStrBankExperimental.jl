```
@static
```

구문 분석 시간에 표현식을 부분적으로 평가합니다.

예를 들어, `@static Sys.iswindows() ? foo : bar`는 `Sys.iswindows()`를 평가하고 표현식에 `foo` 또는 `bar`를 삽입합니다. 이는 다른 플랫폼에서 유효하지 않은 구조가 있을 때 유용합니다. 예를 들어, 존재하지 않는 함수에 대한 `ccall`과 같은 경우입니다. `@static if Sys.isapple() foo end` 및 `@static foo <&&,||> bar`도 유효한 구문입니다.
