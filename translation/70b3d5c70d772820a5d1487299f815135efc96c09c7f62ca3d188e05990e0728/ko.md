```
Sys.isnetbsd([os])
```

NetBSD 파생 OS인지 테스트하는 프레디케이트. [운영 체제 변동 처리](@ref) 문서를 참조하세요.

!!! note
    `Sys.isbsd()`와 혼동하지 마세요. `Sys.isbsd()`는 NetBSD뿐만 아니라 다른 BSD 기반 시스템에서도 `true`입니다. `Sys.isnetbsd()`는 오직 NetBSD만을 참조합니다.


!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.

