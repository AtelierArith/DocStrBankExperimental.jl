```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

전달된 모든 집합을 교차하고 결과로 `s`를 덮어씁니다. 배열의 경우 순서를 유지합니다.

!!! 경고     변형된 인수 중 하나가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.
