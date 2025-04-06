```
LibGit2.CloneOptions
```

[`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: Kullanımda olan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `checkout_opts`: Klonlama işlemi sırasında uzaktan checkout yapmak için seçenekler.
  * `fetch_opts`: Klonlama işlemi sırasında uzaktan ön-checkout fetch yapmak için seçenekler.
  * `bare`: `0` ise, tam uzaktan depo klonlanır. Sıfırdan farklı bir değer ise, kaynak dosyaların yerel kopyası olmayan bir bare klonlama yapılır ve [`gitdir`](@ref) ile [`workdir`](@ref) aynı olur.
  * `localclone`: Yerel bir nesne veritabanını klonlayıp klonlamayacağını veya bir fetch yapıp yapmayacağını belirten bayrak. Varsayılan, git'in karar vermesine izin vermektir. Yerel bir klon için git-bilgilendirilmiş taşıma kullanılmayacak, ancak `file://` ile başlayan URL'ler için kullanılacaktır.
  * `checkout_branch`: Checkout yapılacak dalın adı. Boş bir dize ise, uzaktaki varsayılan dal checkout yapılacaktır.
  * `repository_cb`: Klonlama işleminin yapıldığı *yeni* depoyu oluşturmak için kullanılacak isteğe bağlı geri çağırma.
  * `repository_cb_payload`: Depo geri çağırması için yük.
  * `remote_cb`: Klonlama işlemi yapılmadan önce [`GitRemote`](@ref) oluşturmak için kullanılan isteğe bağlı geri çağırma.
  * `remote_cb_payload`: Uzak geri çağırması için yük.
