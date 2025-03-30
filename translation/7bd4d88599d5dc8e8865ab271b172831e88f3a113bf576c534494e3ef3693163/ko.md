```
bunchkaufman!(A, rook::Bool=false; check = true) -> BunchKaufman
```

`bunchkaufman!`는 [`bunchkaufman`](@ref)와 동일하지만, 복사본을 생성하는 대신 입력 `A`를 덮어써서 공간을 절약합니다.
