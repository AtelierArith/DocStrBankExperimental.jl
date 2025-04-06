```
addprocs(manager::ClusterManager; kwargs...) -> Süreç tanımlayıcılarının listesi
```

Belirtilen küme yöneticisi aracılığıyla işçi süreçlerini başlatır.

Örneğin, Beowulf kümeleri, `ClusterManagers.jl` paketinde uygulanan özel bir küme yöneticisi aracılığıyla desteklenmektedir.

Yeni başlatılan bir işçinin ana makineden bağlantı kurulmasını beklediği saniye sayısı, işçi sürecinin ortamında `JULIA_WORKER_TIMEOUT` değişkeni aracılığıyla belirtilebilir. Sadece TCP/IP taşıma kullanıldığında geçerlidir.

İşçileri REPL'yi veya işçileri programlı olarak başlatıyorsanız içindeki işlevi engellemeden başlatmak için, `addprocs`'ı kendi görevinde çalıştırın.

# Örnekler

```julia
# Meşgul kümelerde, `addprocs`'ı asenkron olarak çağırın
t = @async addprocs(...)
```

```julia
# İşçileri çevrimiçi olduklarında kullanın
if nprocs() > 1   # En az bir yeni işçi mevcut olduğundan emin olun
   ....   # dağıtılmış yürütme gerçekleştirin
end
```

```julia
# Yeni başlatılan işçi kimliklerini veya herhangi bir hata mesajını alın
if istaskdone(t)   # `addprocs`'ın tamamlanıp tamamlanmadığını kontrol edin, böylece `fetch` engellenmez
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```
