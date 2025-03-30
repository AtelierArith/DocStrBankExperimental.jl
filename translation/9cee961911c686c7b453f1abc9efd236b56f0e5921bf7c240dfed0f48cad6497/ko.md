```
eigen!(A; permute, scale, sortby)
eigen!(A, B; sortby)
```

[`eigen`](@ref)와 동일하지만, 복사본을 생성하는 대신 입력 `A`(및 `B`)를 덮어써서 공간을 절약합니다.
