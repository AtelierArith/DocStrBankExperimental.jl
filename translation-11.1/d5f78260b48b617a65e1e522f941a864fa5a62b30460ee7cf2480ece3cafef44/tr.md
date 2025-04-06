```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker`, TCP/IP üzerinden bağlanan işçi süreçleri için varsayılan giriş noktası olan bir iç işlevdir. Süreci bir Julia küme işçisi olarak ayarlar.

host:port bilgisi `out` akışına (varsayılan olarak stdout) yazılır.

Fonksiyon, gerekirse stdin'den çerezi okur ve boş bir portta (veya belirtilmişse, `--bind-to` komut satırı seçeneğindeki portta) dinler ve gelen TCP bağlantılarını ve isteklerini işlemek için görevleri planlar. Ayrıca (isteğe bağlı olarak) stdin'i kapatır ve stderr'yi stdout'a yönlendirir.

Hiçbir şey döndürmez.
