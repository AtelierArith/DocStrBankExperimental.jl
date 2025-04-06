```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

Verilen `(Julia)Artifacts.toml` dosyasında saklanan bir artefakt hakkında (isimle tanımlanan) meta verileri alın. Eğer artefakt platforma özgü ise, en uygun eşleşmeyi seçmek için `platform`'ı kullanın. Eğer hiçbiri bulunamazsa, `nothing` döndürün.

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

