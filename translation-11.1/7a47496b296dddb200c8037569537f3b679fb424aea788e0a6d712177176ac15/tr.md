```
LibGit2.FetchHead
```

Fetch sırasında HEAD hakkında bilgi içerir; bu, fetch edilen dalın adı ve URL'si, HEAD'in oid'si ve fetch edilen HEAD'in yerel olarak birleştirilip birleştirilmediğini içerir.

Alanlar şunları temsil eder:

  * `name`: Fetch head'in yerel referans veritabanındaki adı, örneğin,  `"refs/heads/master"`.
  * `url`: Fetch head'in URL'si.
  * `oid`: Fetch head'in ucunun [`GitHash`](@ref).
  * `ismerge`: Uzakta yapılan değişikliklerin yerel kopyaya henüz birleştirilip birleştirilmediğini belirten Boolean bayrağı. Eğer `true` ise, yerel kopya uzak fetch head ile günceldir.
