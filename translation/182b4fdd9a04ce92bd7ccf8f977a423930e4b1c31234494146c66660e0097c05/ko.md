```
mapfoldl(f, op, itr; [init])
```

[`mapreduce`](@ref)와 유사하지만, [`foldl`](@ref)처럼 왼쪽 결합성을 보장합니다. 제공된 경우, 키워드 인수 `init`은 정확히 한 번 사용됩니다. 일반적으로 빈 컬렉션과 작업하기 위해 `init`을 제공해야 합니다.
