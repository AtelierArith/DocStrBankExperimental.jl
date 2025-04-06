```
LibGit2.DiffFile
```

Delta'nın bir tarafının tanımı. [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `id`: farktaki öğenin [`GitHash`](@ref). Eğer öğe bu farkın bu tarafında boşsa (örneğin, bir dosyanın kaldırılmasına dair bir farksa), bu `GitHash(0)` olacaktır.
  * `path`: depo çalışma dizinine göre öğeye giden `NULL` ile sonlandırılmış bir yol.
  * `size`: öğenin boyutu bayt cinsinden.
  * `flags`: [`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t) bayraklarının bir kombinasyonu. Bu tam sayının `i`'nci biti `i`'nci bayrağı ayarlar.
  * `mode`: öğe için [`stat`](@ref) modu.
  * `id_abbrev`: yalnızca LibGit2 sürümleri `0.25.0` veya daha yenisi için mevcuttur. [`string`](@ref) kullanılarak dönüştürüldüğünde `id` alanının uzunluğu. Genellikle `OID_HEXSZ` (40) ile eşittir.
