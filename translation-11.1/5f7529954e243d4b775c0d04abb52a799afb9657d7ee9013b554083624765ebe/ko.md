```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

지정된 플랫폼에 축소된 아티팩트의 해시를 반환하는 `artifact_meta()`에 대한 얇은 래퍼입니다. 매핑을 찾을 수 없는 경우 `nothing`을 반환합니다.

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

