```
launch(manager::ClusterManager, params::Dict, launched::Array, launch_ntfy::Condition)
```

Küme yöneticileri tarafından uygulanır. Bu işlev tarafından başlatılan her Julia işçisi için, `launched` dizisine bir `WorkerConfig` girişi eklemeli ve `launch_ntfy`'yi bildirmelidir. İşlev, `manager` tarafından talep edilen tüm işçilerin başlatılmasıyla birlikte çıkmalıdır. `params`, [`addprocs`](@ref) ile çağrılan tüm anahtar kelime argümanlarının bir sözlüğüdür.
