```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

Verilen `Artifacts.toml` dosyasından istenen platform için indirilmesi gereken her bir artefaktı içeren bir sözlük döndürür. Eğer `include_lazy` ayarı yapılmışsa, tembel artefaktlar da dahil edilir.
