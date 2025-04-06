```
open(command, mode::AbstractString, stdio=devnull)
```

`command`'ı asenkron olarak çalıştırın. `open(command, stdio; read, write)` gibi, ancak okuma ve yazma bayraklarını anahtar argümanlar yerine bir mod dizesi aracılığıyla belirterek. Olası mod dizeleri şunlardır:

| Mod  | Açıklama     | Anahtar Kelimeler           |
|:---- |:------------ |:--------------------------- |
| `r`  | okuma        | yok                         |
| `w`  | yazma        | `write = true`              |
| `r+` | okuma, yazma | `read = true, write = true` |
| `w+` | okuma, yazma | `read = true, write = true` |
