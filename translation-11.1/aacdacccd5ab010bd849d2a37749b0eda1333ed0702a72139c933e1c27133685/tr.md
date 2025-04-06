```
LibGit2.RebaseOperation
```

Rebase sırasında gerçekleştirilecek tek bir talimat/işlemi tanımlar. [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `optype`: şu anda gerçekleştirilen rebase işleminin türü. Seçenekler şunlardır:

      * `REBASE_OPERATION_PICK`: söz konusu commit'i cherry-pick yap.
      * `REBASE_OPERATION_REWORD`: söz konusu commit'i cherry-pick yap, ancak mesajını istemle yeniden yaz.
      * `REBASE_OPERATION_EDIT`: söz konusu commit'i cherry-pick yap, ancak kullanıcının commit'in içeriğini ve mesajını düzenlemesine izin ver.
      * `REBASE_OPERATION_SQUASH`: söz konusu commit'i önceki commit'e squash yap. İki commit'in mesajları birleştirilecektir.
      * `REBASE_OPERATION_FIXUP`: söz konusu commit'i önceki commit'e squash yap. Sadece önceki commit'in mesajı kullanılacaktır.
      * `REBASE_OPERATION_EXEC`: bir commit'i cherry-pick yapma. Bir komut çalıştır ve komut başarılı bir şekilde çıkarsa devam et.
  * `id`: bu rebase adımında üzerinde çalışılan commit'in [`GitHash`](@ref).
  * `exec`: `REBASE_OPERATION_EXEC` kullanılıyorsa, bu adımda çalıştırılacak komut (örneğin, her commit'ten sonra test paketini çalıştırmak).
