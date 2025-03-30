```
init_worker(cookie::AbstractString, manager::ClusterManager=DefaultClusterManager())
```

Özel taşımaları uygulayan küme yöneticileri tarafından çağrılır. Yeni başlatılan bir süreci işçi olarak başlatır. Komut satırı argümanı `--worker[=<cookie>]`, bir süreci işçi olarak başlatma etkisine sahiptir ve taşımada TCP/IP soketlerini kullanır. `cookie`, bir [`cluster_cookie`](@ref) dir.
