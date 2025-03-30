```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

빈 `AbstractDict` 컨테이너를 생성하여 `index_type` 유형의 인덱스와 `value_type` 유형의 값을 수용할 수 있습니다. 두 번째 및 세 번째 인수는 선택 사항이며 각각 입력의 `keytype` 및 `valtype`으로 기본 설정됩니다. (두 유형 중 하나만 지정된 경우, 이는 `value_type`으로 간주되며, 기본적으로 `index_type`은 `keytype(a)`로 설정됩니다).

사용자 정의 `AbstractDict` 하위 유형은 세 개의 인수를 사용하는 서명에 특화하여 주어진 인덱스 및 값 유형에 가장 적합한 특정 사전 유형을 선택할 수 있습니다. 기본값은 빈 `Dict`를 반환하는 것입니다.
