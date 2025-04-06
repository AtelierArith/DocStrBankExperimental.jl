```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

주어진 아티팩트(sha1 git 트리 해시로 식별됨)가 디스크에 존재하는지 여부를 반환합니다. 주어진 아티팩트가 여러 위치(예: 여러 저장소 내)에 존재할 수 있다는 점에 유의하십시오.

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

