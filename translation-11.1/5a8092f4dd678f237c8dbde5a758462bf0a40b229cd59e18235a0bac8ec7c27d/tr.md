```
LibGit2.MergeOptions
```

[`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: yapının kullanımda olan versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `flags`: birleştirme davranışını tanımlayan bayraklar için bir `enum`. [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95) içinde tanımlanmıştır. Karşılık gelen Julia enum'u `GIT_MERGE` ve değerleri şunlardır:

      * `MERGE_FIND_RENAMES`: bir dosyanın ortak ata ile "bizim" veya "onların" tarafı arasında yeniden adlandırılıp adlandırılmadığını tespit et. Bir dosyanın yeniden adlandırıldığı durumlarda birleştirmelere izin verir.
      * `MERGE_FAIL_ON_CONFLICT`: bir çelişki bulunursa hemen çık, çözmeye çalışmak yerine.
      * `MERGE_SKIP_REUC`: birleştirmeden kaynaklanan dizinde REUC uzantısını yazma.
      * `MERGE_NO_RECURSIVE`: birleştirilen commit'lerin birden fazla birleştirme tabanı varsa, bunları yeniden birleştirmeye çalışmak yerine ilkini kullan.
  * `rename_threshold`: iki dosyanın birinin diğerinin yeniden adı olarak kabul edilmesi için ne kadar benzer olması gerektiği. Bu, yüzde benzerliğini ayarlayan bir tam sayıdır. Varsayılan 50'dir.
  * `target_limit`: yeniden adlandırmaları aramak için karşılaştırılacak maksimum dosya sayısı. Varsayılan 200'dür.
  * `metric`: yeniden adlandırma tespiti için iki dosya arasındaki benzerliği belirlemek için kullanılacak isteğe bağlı özel işlev.
  * `recursion_limit`: yeni sanal birleştirme tabanı oluşturmak için gerçekleştirilecek ortak ataların birleştirme sayısında üst sınır. Varsayılan sınırsızdır. Bu alan yalnızca 0.24.0'dan daha yeni libgit2 sürümlerinde mevcuttur.
  * `default_driver`: her iki tarafın da değiştiği durumlarda kullanılacak birleştirme sürücüsü. Bu alan yalnızca 0.25.0'dan daha yeni libgit2 sürümlerinde mevcuttur.
  * `file_favor`: `text` sürücüsü için çelişen dosya içeriklerini nasıl ele alacağınız.

      * `MERGE_FILE_FAVOR_NORMAL`: birleştirmenin her iki tarafında bir bölümde değişiklik varsa, çelişkiyi `git checkout`'un birleştirme dosyası oluşturmak için kullanacağı dizinde not edin, kullanıcı daha sonra çelişkileri çözmek için buna başvurabilir. Bu varsayılandır.
      * `MERGE_FILE_FAVOR_OURS`: birleştirmenin her iki tarafında bir bölümde değişiklik varsa, dizinde "bizim" tarafındaki versiyonu kullan.
      * `MERGE_FILE_FAVOR_THEIRS`: birleştirmenin her iki tarafında bir bölümde değişiklik varsa, dizinde "onların" tarafındaki versiyonu kullan.
      * `MERGE_FILE_FAVOR_UNION`: birleştirmenin her iki tarafında bir bölümde değişiklik varsa, dizine konulan dosyada her iki taraftan da her benzersiz satırı dahil et.
  * `file_flags`: dosyaları birleştirme için kılavuzlar.
