```
stat(file)
```

Bir yapıyı döndürür; bu yapının alanları dosya hakkında bilgi içerir. Yapının alanları şunlardır:

| İsim    | Tür                             | Açıklama                                                                 |
|:------- |:------------------------------- |:------------------------------------------------------------------------ |
| desc    | `Union{String, Base.OS_HANDLE}` | Yol veya OS dosya tanımlayıcısı                                          |
| size    | `Int64`                         | Dosyanın boyutu (bayt cinsinden)                                         |
| device  | `UInt`                          | Dosyayı içeren cihazın kimliği                                           |
| inode   | `UInt`                          | Dosyanın inode numarası                                                  |
| mode    | `UInt`                          | Dosyanın koruma modu                                                     |
| nlink   | `Int`                           | Dosyaya bağlı sert bağlantı sayısı                                       |
| uid     | `UInt`                          | Dosya sahibinin kullanıcı kimliği                                        |
| gid     | `UInt`                          | Dosya sahibinin grup kimliği                                             |
| rdev    | `UInt`                          | Bu dosya bir cihaza atıfta bulunuyorsa, atıfta bulunduğu cihazın kimliği |
| blksize | `Int64`                         | Dosya için dosya sistemi tercih edilen blok boyutu                       |
| blocks  | `Int64`                         | Ayrılan 512 baytlık blok sayısı                                          |
| mtime   | `Float64`                       | Dosyanın en son ne zaman değiştirildiğinin Unix zaman damgası            |
| ctime   | `Float64`                       | Dosyanın meta verilerinin ne zaman değiştirildiğinin Unix zaman damgası  |
