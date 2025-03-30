```
ImmutableDict
```

`ImmutableDict`는 불변 연결 리스트로 구현된 사전으로, 많은 개별 삽입을 통해 구성된 작은 사전에 최적화되어 있습니다. 값을 제거하는 것은 불가능하지만, 동일한 키로 새 값을 삽입하여 부분적으로 덮어쓰고 숨길 수 있습니다.

```
ImmutableDict(KV::Pair)
```

`key => value` 쌍에 대한 `ImmutableDict`에 새 항목을 만듭니다.

  * `(key => value) in dict`를 사용하여 이 특정 조합이 속성 집합에 있는지 확인합니다.
  * `get(dict, key, default)`를 사용하여 특정 키에 대한 가장 최근 값을 검색합니다.
