```
Sys.isfreebsd([os])
```

FreeBSD 파생 OS인지 테스트하는 술어입니다. [운영 체제 변동 처리](@ref)에서 문서를 참조하세요.

!!! note
    `Sys.isbsd()`와 혼동하지 마세요. `Sys.isbsd()`는 FreeBSD뿐만 아니라 다른 BSD 기반 시스템에서도 `true`입니다. `Sys.isfreebsd()`는 오직 FreeBSD만을 참조합니다.


!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.

