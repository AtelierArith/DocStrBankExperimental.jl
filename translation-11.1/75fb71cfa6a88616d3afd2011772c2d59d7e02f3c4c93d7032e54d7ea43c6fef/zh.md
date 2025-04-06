```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

返回一个字典，其中每个条目都是来自给定 `Artifacts.toml` 的应为请求的平台下载的工件。如果设置了 `include_lazy`，则包括延迟工件。
