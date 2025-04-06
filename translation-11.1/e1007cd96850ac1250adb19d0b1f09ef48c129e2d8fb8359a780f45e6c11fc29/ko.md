```
Sys.isopenbsd([os])
```

OpenBSD 파생판인지 테스트하는 프레디케이트. [운영 체제 변동 처리](@ref)에서 문서를 참조하십시오.

!!! note
    OpenBSD에서 `true`이지만 다른 BSD 기반 시스템에서도 `true`인 `Sys.isbsd()`와 혼동하지 마십시오. `Sys.isopenbsd()`는 OpenBSD에만 해당합니다.


!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.

