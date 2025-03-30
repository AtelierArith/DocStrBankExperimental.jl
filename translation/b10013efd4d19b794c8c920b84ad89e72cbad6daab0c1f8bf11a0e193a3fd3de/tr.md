```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

Yeni bir `Cmd` nesnesi oluşturun, `cmd`'den bir dış program ve argümanları temsil ederken, isteğe bağlı anahtar argümanların ayarlarını değiştirin:

  * `ignorestatus::Bool`: Eğer `true` ise (varsayılan `false`), o zaman `Cmd` sıfır olmayan bir dönüş kodu varsa hata fırlatmayacaktır.
  * `detach::Bool`: Eğer `true` ise (varsayılan `false`), o zaman `Cmd` yeni bir işlem grubunda çalıştırılacak, böylece `julia` işlemini aşacak ve Ctrl-C'nin ona geçmesini engelleyecektir.
  * `windows_verbatim::Bool`: Eğer `true` ise (varsayılan `false`), o zaman Windows'ta `Cmd` argümanları içeren boşluklar da dahil olmak üzere, argümanların alıntılanmadan veya kaçış karakteri olmadan işleme bir komut satırı dizesi gönderecektir. (Windows'ta, argümanlar bir programa tek bir "komut satırı" dizesi olarak gönderilir ve programlar bunu argümanlara ayırmaktan sorumludur. Varsayılan olarak, boş argümanlar ve boşluk veya sekme içeren argümanlar komut satırında çift tırnak `"` ile alıntılanır ve `\` veya `"` karakterleri önüne ters eğik çizgi konularak gönderilir. `windows_verbatim=true`, komut satırını standart dışı yollarla ayrıştıran programları başlatmak için yararlıdır.) Diğer işletim sistemlerinde etkisi yoktur.
  * `windows_hide::Bool`: Eğer `true` ise (varsayılan `false`), o zaman Windows'ta `Cmd` çalıştırıldığında yeni bir konsol penceresi görüntülenmeyecektir. Eğer zaten açık bir konsol varsa veya diğer işletim sistemlerinde etkisi yoktur.
  * `env`: `Cmd`'yi çalıştırırken kullanılacak ortam değişkenlerini ayarlayın. `env`, dizeleri dizelere eşleyen bir sözlük, `"var=val"` biçiminde bir dizi dize veya `"var"=>val` çiftlerinden oluşan bir dizi veya demet olabilir. Mevcut ortamı değiştirmek (yerine koymak yerine) için `env`'yi `copy(ENV)` ile başlatın ve ardından `env["var"]=val` olarak ayarlayın. Tüm öğeleri değiştirmeden bir `Cmd` nesnesi içinde bir ortam bloğuna eklemek için, güncellenmiş ortamla bir `Cmd` nesnesi döndürecek olan [`addenv()`](@ref) fonksiyonunu kullanın.
  * `dir::AbstractString`: Komut için bir çalışma dizini belirtin (mevcut dizin yerine).

Belirtilmeyen anahtarlar için, `cmd`'den mevcut ayarlar kullanılır.

`Cmd(exec)` yapıcısının `exec`'in bir kopyasını oluşturmadığını unutmayın. `exec`'teki sonraki değişiklikler `Cmd` nesnesinde yansıtılacaktır.

Bir `Cmd` nesnesi oluşturmanın en yaygın yolu komut literalleri (ters tırnaklar) iledir, örneğin:

```
`ls -l`
```

Bu daha sonra ayarlarını değiştirmek için `Cmd` yapıcısına geçirilebilir, örneğin:

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
