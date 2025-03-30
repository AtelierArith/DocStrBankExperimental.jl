```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> Süreç tanımlayıcılarının listesi
```

Yerel ana bilgisayarda `np` işçilerini yerleşik `LocalManager` kullanarak başlatın.

Yerel işçiler, ana süreçten mevcut paket ortamını (yani, aktif proje, [`LOAD_PATH`](@ref) ve [`DEPOT_PATH`](@ref)) miras alır.

!!! uyarı     İşçilerin `~/.julia/config/startup.jl` başlangıç betiğini çalıştırmadığını ve diğer çalışan süreçlerle küresel durumlarını (komut satırı anahtarları, küresel değişkenler, yeni yöntem tanımları ve yüklenen modüller gibi) senkronize etmediğini unutmayın.

**Anahtar argümanlar**:

  * `restrict::Bool`: `true` (varsayılan) ise, bağlama `127.0.0.1` ile sınırlıdır.
  * `dir`, `exename`, `exeflags`, `env`, `topology`, `lazy`, `enable_threaded_blas`: `SSHManager` için olduğu gibi aynı etki, [`addprocs(machines::AbstractVector)`](@ref) belgelerine bakın.

!!! uyumluluk "Julia 1.9"
    Paket ortamının miras alınması ve `env` anahtar argümanı Julia 1.9'da eklendi.

