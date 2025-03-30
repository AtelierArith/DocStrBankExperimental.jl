```
@distributed
```

분산 메모리, 병렬 for 루프의 형태:

```
@distributed [reducer] for var = range
    body
end
```

지정된 범위는 분할되어 모든 작업자에서 로컬로 실행됩니다. 선택적 리듀서 함수가 지정된 경우, `@distributed`는 각 작업자에서 로컬 축소를 수행하고 호출 프로세스에서 최종 축소를 수행합니다.

리듀서 함수 없이 `@distributed`는 비동기적으로 실행되며, 즉 모든 사용 가능한 작업자에서 독립적인 작업을 생성하고 완료를 기다리지 않고 즉시 반환합니다. 완료를 기다리려면 호출을 [`@sync`](@ref)로 접두어를 붙여야 합니다, 예를 들어:

```
@sync @distributed for var = range
    body
end
```
