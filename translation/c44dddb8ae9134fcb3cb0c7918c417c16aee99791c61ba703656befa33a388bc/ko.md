```
Base.checked_length(r)
```

`length(r)`를 계산하지만, 결과가 `Union{Integer(eltype(r)),Int}`에 맞지 않을 경우 오버플로우 오류를 확인할 수 있습니다.
