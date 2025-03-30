```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

주어진 `(Julia)Artifacts.toml` 파일에 저장된 주어진 아티팩트(이름으로 식별됨)에 대한 메타데이터를 가져옵니다. 아티팩트가 플랫폼 특정인 경우, `platform`을 사용하여 가장 적합한 매핑을 선택합니다. 찾을 수 없는 경우 `nothing`을 반환합니다.

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

