```
LibGit2.DescribeOptions
```

[`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: bu yapının kullanımda olan versiyonu, eğer bu daha sonra değişirse. Şu anda her zaman `1`.
  * `max_candidates_tags`: bir komiti tanımlamak için `refs/tags` içindeki en son bu kadar çok etiketi dikkate al. Varsayılan olarak 10'dur (yani en son 10 etiketi incelemek için).
  * `describe_strategy`: `refs/tags` içindeki tüm girişleri dikkate alıp almayacağı (eşdeğer olarak `git-describe --tags`) veya `refs/` içindeki tüm girişleri (eşdeğer olarak `git-describe --all`). Varsayılan olarak yalnızca anotasyonlu etiketler gösterilir. Eğer `Consts.DESCRIBE_TAGS` geçirilirse, anotasyonlu veya anotasyonsuz tüm etiketler dikkate alınacaktır. Eğer `Consts.DESCRIBE_ALL` geçirilirse, `refs/` içindeki herhangi bir ref dikkate alınacaktır.
  * `pattern`: yalnızca `pattern` ile eşleşen etiketleri dikkate al. Glob genişletmesini destekler.
  * `only_follow_first_parent`: eşleşen bir referanstan tanımlanan nesneye olan mesafeyi bulurken, yalnızca ilk ebeveynden olan mesafeyi dikkate al.
  * `show_commit_oid_as_fallback`: eğer bir komiti tanımlayan eşleşen bir referans bulunamazsa, bir hata fırlatmak yerine komitin [`GitHash`](@ref) değerini göster. (varsayılan davranış).
