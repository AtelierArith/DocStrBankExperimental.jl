Bir yapılandırma dosyasının öncelik seviyesi.

Bu öncelik seviyeleri, git'te yapılandırma girişlerini ararken doğal yükselme mantığına (yüksekten düşüğe) karşılık gelir.

  * `CONFIG_LEVEL_DEFAULT` - Mevcutsa, global, XDG ve sistem yapılandırma dosyalarını açın.
  * `CONFIG_LEVEL_PROGRAMDATA` - Taşınabilir git ile uyumluluk için Windows'ta sistem genelinde
  * `CONFIG_LEVEL_SYSTEM` - Sistem genelinde yapılandırma dosyası; Linux sistemlerinde `/etc/gitconfig`
  * `CONFIG_LEVEL_XDG` - XDG uyumlu yapılandırma dosyası; genellikle `~/.config/git/config`
  * `CONFIG_LEVEL_GLOBAL` - Kullanıcıya özel yapılandırma dosyası (aynı zamanda Global yapılandırma dosyası olarak da adlandırılır); genellikle `~/.gitconfig`
  * `CONFIG_LEVEL_LOCAL` - Depoya özel yapılandırma dosyası; bare olmayan reposlarda `$WORK_DIR/.git/config`
  * `CONFIG_LEVEL_APP` - Uygulamaya özel yapılandırma dosyası; uygulamalar tarafından serbestçe tanımlanır
  * `CONFIG_HIGHEST_LEVEL` - Mevcut en yüksek seviye yapılandırma dosyasını temsil eder (yani, gerçekten yüklenen en spesifik yapılandırma dosyası)
