```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

Belirtilen `rmt` uzak git deposundan `refspecs` kullanarak hangi uzak dal(lar)ın alınacağını belirleyerek alın. Anahtar kelime argümanları şunlardır:

  * `options`: alım için seçenekleri belirler, örneğin sonrasında temizleyip temizlemeyeceği. Daha fazla bilgi için [`FetchOptions`](@ref) bölümüne bakın.
  * `msg`: reflog'lara eklemek için bir mesaj.
