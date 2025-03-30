```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

Belirtilen, platforma göre çökertilmiş artefaktın hash'ini döndürmek için `artifact_meta()` etrafında ince bir sarmalayıcı. Herhangi bir eşleme bulunamazsa `nothing` döner.

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

