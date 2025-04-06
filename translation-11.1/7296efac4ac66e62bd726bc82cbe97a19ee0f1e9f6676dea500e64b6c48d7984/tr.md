```
LibGit2.DiffOptionsStruct
```

[`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `flags`: hangi dosyaların diff'te görüneceğini kontrol eden bayraklar. Varsayılan `DIFF_NORMAL`'dır.
  * `ignore_submodules`: alt modüllerdeki dosyaları kontrol edip etmeyeceği. Varsayılan `SUBMODULE_IGNORE_UNSPECIFIED`'dir, bu da alt modülün yapılandırmasının diff'te görünüp görünmeyeceğini kontrol edeceği anlamına gelir.
  * `pathspec`: diff'e dahil edilecek dosyaların yolu. Varsayılan, depodaki tüm dosyaları kullanmaktır.
  * `notify_cb`: dosya delta'ları eklendikçe diff'teki değişiklikleri kullanıcıya bildirecek isteğe bağlı geri çağırma.
  * `progress_cb`: diff ilerlemesini gösterecek isteğe bağlı geri çağırma. Sadece libgit2'nin en az 0.24.0 sürümünde geçerlidir.
  * `payload`: `notify_cb` ve `progress_cb`'ye iletilecek yük.
  * `context_lines`: bir hunk'ın kenarlarını tanımlamak için kullanılan *değişmeyen* satır sayısı. Bu, bir hunk'tan önce/sonra gösterilecek satır sayısıdır. Varsayılan 3'tür.
  * `interhunk_lines`: iki ayrı hunk arasında birleştirilmeden önce izin verilen maksimum *değişmeyen* satır sayısı. Varsayılan 0'dır.
  * `id_abbrev`: yazdırılacak kısaltılmış [`GitHash`](@ref) uzunluğunu ayarlar. Varsayılan `7`'dir.
  * `max_size`: bir blob'un maksimum dosya boyutu. Bu boyuttan büyükse, ikili blob olarak işlenecektir. Varsayılan 512 MB'dir.
  * `old_prefix`: diff'in bir tarafında eski dosyaları yerleştirmek için sanal dosya dizini. Varsayılan `"a"`dır.
  * `new_prefix`: diff'in bir tarafında yeni dosyaları yerleştirmek için sanal dosya dizini. Varsayılan `"b"`dir.
