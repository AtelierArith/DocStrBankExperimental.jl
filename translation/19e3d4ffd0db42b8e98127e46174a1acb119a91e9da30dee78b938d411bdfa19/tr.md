`Header` türü, bir tar dosyasındaki tek bir kaydın temel meta verilerini temsil eden bir yapıdır ve tanımı şu şekildedir:

```
struct Header
    path :: String # kök ile ilgili yol
    type :: Symbol # tür göstergesi (aşağıya bakınız)
    mode :: UInt16 # mod/izinler (en iyi sekizli olarak görüntülenir)
    size :: Int64  # kayıt verisinin boyutu bayt cinsinden
    link :: String # bir sembolik bağlantının hedef yolu
end
```

Türler aşağıdaki sembollerle temsil edilir: `file`, `hardlink`, `symlink`, `chardev`, `blockdev`, `directory`, `fifo`, veya bilinmeyen türler için, sembol olarak typeflag karakteri. Not edin ki [`extract`](@ref) `file`, `symlink` ve `directory` dışındaki kayıt türlerini çıkarmayı reddeder; [`list`](@ref) ise yalnızca `strict=false` ile çağrıldığında diğer türdeki kayıtları listeleyecektir.

Tar formatı, kullanıcı ve grup kimlikleri, kullanıcı ve grup adları ve zaman damgaları da dahil olmak üzere kayıtlar hakkında çeşitli diğer meta verileri içerir. `Tar` paketi, tasarımı gereği, bunları tamamen göz ardı eder. Tar dosyaları oluştururken, bu alanlar her zaman sıfır/boş olarak ayarlanır. Tar dosyaları okunurken, bu alanlar yalnızca her bir başlık kaydı için başlık kontrol toplamlarını doğrulamak dışında göz ardı edilir.
