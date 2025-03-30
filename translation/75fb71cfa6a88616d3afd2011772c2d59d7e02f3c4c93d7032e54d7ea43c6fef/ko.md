```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

요청된 플랫폼에 대해 다운로드해야 하는 `Artifacts.toml`의 모든 항목이 포함된 사전을 반환합니다. `include_lazy`가 설정된 경우 지연 아티팩트가 포함됩니다.
