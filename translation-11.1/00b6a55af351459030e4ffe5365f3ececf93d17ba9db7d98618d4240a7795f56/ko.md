```
Base.issingletontype(T)
```

타입 `T`가 정확히 하나의 가능한 인스턴스를 가지고 있는지 확인합니다. 예를 들어, 다른 싱글톤 값 외에 필드가 없는 구조체 타입입니다. 만약 `T`가 구체적인 타입이 아니라면 `false`를 반환합니다.
