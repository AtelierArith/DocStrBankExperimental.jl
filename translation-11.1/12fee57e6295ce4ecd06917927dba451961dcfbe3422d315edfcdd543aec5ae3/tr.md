```
LibGit2.BlameOptions
```

[`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `flags`: `Consts.BLAME_NORMAL` veya `Consts.BLAME_FIRST_PARENT`'dan biri (diğer blame bayrakları henüz libgit2 tarafından uygulanmamıştır).
  * `min_match_characters`: bir committe değişikliklerin o commit ile ilişkilendirilmesi için gereken minimum *alfa sayısal* karakter sayısı. Varsayılan 20'dir. Sadece `Consts.BLAME_*_COPIES` bayraklarından biri kullanıldığında geçerlidir, bu da libgit2 tarafından henüz uygulanmamıştır.
  * `newest_commit`: değişikliklere bakılacak en yeni commitin [`GitHash`](@ref).
  * `oldest_commit`: değişikliklere bakılacak en eski commitin [`GitHash`](@ref).
  * `min_line`: blame işlemine başlanacak dosyanın ilk satırı. Varsayılan `1`'dir.
  * `max_line`: blame işleminin yapılacağı dosyanın son satırı. Varsayılan `0`'dır, bu da dosyanın son satırını ifade eder.
