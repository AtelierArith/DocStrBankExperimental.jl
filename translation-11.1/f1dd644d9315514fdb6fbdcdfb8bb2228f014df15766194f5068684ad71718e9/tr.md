```
LibGit2.StatusOptions
```

`git_status_foreach_ext()`'in geri çağırmaları nasıl vereceğini kontrol etmek için seçenekler. [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `show`: hangi dosyaların inceleneceği ve hangi sırayla inceleneceği için bir bayrak. Varsayılan `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`.
  * `flags`: bir durum çağrısında kullanılan geri çağırmaları kontrol etmek için bayraklar.
  * `pathspec`: yol eşleştirmesi için kullanılacak bir dizi yol. Yol eşleştirme davranışı, `show` ve `flags` değerlerine bağlı olarak değişecektir.
  * `baseline`, çalışma dizini ve dizin ile karşılaştırma için kullanılacak ağaçtır; varsayılan HEAD'dir.
