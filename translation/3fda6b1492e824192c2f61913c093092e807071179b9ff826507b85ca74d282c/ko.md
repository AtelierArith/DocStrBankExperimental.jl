```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

주어진 아티팩트(SHA1 git 트리 해시로 식별됨)의 설치 경로를 반환합니다. 아티팩트가 존재하지 않으면 설치될 위치를 반환합니다.

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

