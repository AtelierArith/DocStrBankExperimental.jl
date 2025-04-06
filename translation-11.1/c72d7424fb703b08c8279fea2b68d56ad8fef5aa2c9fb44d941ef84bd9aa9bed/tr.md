# macOS

Mevcut Xcode komut satırı araçlarının yüklü olması gerekir: terminalde `xcode-select --install` komutunu çalıştırın. Her macOS güncellemesinden sonra bu terminal komutunu yeniden çalıştırmanız gerekecek, aksi takdirde eksik kütüphaneler veya başlıklarla ilgili hatalarla karşılaşabilirsiniz.

Bağımlı kütüphaneler artık [BinaryBuilder](https://binarybuilder.org) ile derlenmiştir ve otomatik olarak indirilecektir. Bu, Julia kaynaklarını derlemenin tercih edilen yoludur. Hepsini kendiniz derlemek isterseniz, Julia bağımlılıklarını derlemek için 64-bit gfortran'a ihtiyacınız olacak.

```bash
brew install gcc
```

Eğer `.bashrc` veya eşdeğeri dosyada `LD_LIBRARY_PATH` veya `DYLD_LIBRARY_PATH` ayarladıysanız, Julia ile birlikte gelen çeşitli kütüphaneleri bulamayabilir. Julia'nın çalışabilmesi için bu ortam değişkenlerinin kaldırılması gerekir.
