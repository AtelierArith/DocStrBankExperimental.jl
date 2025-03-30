```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

[`asyncmap`](@ref)와 유사하지만, 컬렉션을 반환하는 대신 `results`에 출력을 저장합니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.
