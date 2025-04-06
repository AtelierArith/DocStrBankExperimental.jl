```
find_library(names [, locations])
```

`names` 목록에서 `locations` 목록의 경로, `DL_LOAD_PATH` 또는 시스템 라이브러리 경로(그 순서대로)에서 성공적으로 dlopen할 수 있는 첫 번째 라이브러리를 검색합니다. 성공 시, 반환 값은 이름 중 하나가 될 것이며(잠재적으로 locations의 경로 중 하나로 접두사가 붙을 수 있음) 이 문자열은 `global const`에 할당되어 향후 `ccall`에서 라이브러리 이름으로 사용될 수 있습니다. 실패 시, 빈 문자열을 반환합니다.
