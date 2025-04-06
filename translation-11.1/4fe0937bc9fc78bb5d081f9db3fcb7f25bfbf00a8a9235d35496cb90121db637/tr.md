```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

[`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create) etrafında bir sarmalayıcı. `repo` içinde bir commit oluşturur. `msg` commit mesajıdır. Yeni commit'in OID'sini döndürür.

Anahtar kelime argümanları şunlardır:

  * `refname::AbstractString=Consts.HEAD_FILE`: NULL değilse, yeni commit'e işaret edecek referansın adı. Örneğin, `"HEAD"` mevcut dalın HEAD'ini günceller. Referans henüz mevcut değilse, oluşturulacaktır.
  * `author::Signature = Signature(repo)` commit'i yazan kişinin bilgilerini içeren bir `Signature`'dır.
  * `committer::Signature = Signature(repo)` commit'i depoya ekleyen kişinin bilgilerini içeren bir `Signature`'dır. Mutlaka `author` ile aynı değildir; örneğin, `author` bir patch'i `committer`'a e-posta ile gönderip, `committer` bunu ekleyebilir.
  * `tree_id::GitHash = GitHash()` commit oluşturmak için kullanılacak bir git ağacıdır; soyunu ve diğer tarihlerle olan ilişkisini gösterir. `tree` `repo`ya ait olmalıdır.
  * `parent_ids::Vector{GitHash}=GitHash[]` yeni commit için ebeveyn commit'leri olarak kullanılacak [`GitHash`](@ref) listesi ve boş olabilir. Bir commit, örneğin bir birleştirme commit'i ise birden fazla ebeveyn içerebilir.
