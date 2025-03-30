```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

Belirtilen `rmt` uzak git deposuna `refspecs` kullanarak hangi uzak dal(lar)a itileceğini belirleyerek itme yapar. Anahtar argümanlar şunlardır:

  * `force`: `true` ise, çatışmaları göz ardı ederek zorla itme yapılır.
  * `options`: itme için seçenekleri belirler, örneğin hangi proxy başlıklarının kullanılacağını. Daha fazla bilgi için [`PushOptions`](@ref) kısmına bakın.

!!! note
    İtme refspecleri hakkında bilgi eklemenin iki başka yolu vardır: bir seçenek ayarlamak için deponun `GitConfig`'inde (`push.default` anahtarı ile) veya [`add_push!`](@ref) çağrısını yaparak. Aksi takdirde, `push` çağrısında bir itme refspec'ini açıkça belirtmeniz gerekecektir, böylece etkili olur, örneğin: `LibGit2.push(repo, refspecs=["refs/heads/master"])`.

