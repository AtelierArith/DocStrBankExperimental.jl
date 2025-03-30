```
LibGit2.DescribeFormatOptions
```

[`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `abbreviated_size`: kullanılacak kısaltılmış `GitHash`'in boyutu için alt sınır, varsayılan olarak `7`.
  * `always_use_long_format`: kısa bir format kullanılabilse bile, dizeler için uzun formatı kullanmak üzere `1` olarak ayarlanır.
  * `dirty_suffix`: ayarlandığında, bu, [`workdir`](@ref) kirli olduğunda açıklama dizesinin sonuna eklenecektir.
