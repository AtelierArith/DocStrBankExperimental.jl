```
Sys.isbsd([os])
```

OS가 BSD의 파생인지 테스트하는 술어입니다. [운영 체제 변동 처리](@ref)에서 문서를 참조하세요.

!!! note
    Darwin 커널은 BSD에서 파생되었으므로 `Sys.isbsd()`는 macOS 시스템에서 `true`입니다. 술어에서 macOS를 제외하려면 `Sys.isbsd() && !Sys.isapple()`을 사용하세요.

