```
define_editor(fn, pattern; wait=false)
```

Yeni bir `pattern` ile eşleşen editör tanımlayın, bu editör bir dosyayı (belirli bir satır numarasına göre) `fn` kullanarak açmak için kullanılabilir.

`fn` argümanı, verilen editör ile bir dosyayı nasıl açacağınızı belirleyen bir işlevdir. Aşağıdaki dört argümanı almalıdır:

  * `cmd` - editör için bir temel komut nesnesi
  * `path` - açılacak kaynak dosyanın yolu
  * `line` - editörü açmak için kullanılacak satır numarası
  * `column` - editörü açmak için kullanılacak sütun numarası

Belirli bir satıra veya belirli bir sütuna açamayan editörler `line` ve/veya `column` argümanını göz ardı edebilir. `fn` geri çağrısı, bir dosyayı açmak için uygun bir `Cmd` nesnesi döndürmeli veya bu dosyayı düzenleyemeyeceklerini belirtmek için `nothing` döndürmelidir. Bu editörün mevcut ortam için uygun olmadığını belirtmek için `nothing` kullanın ve başka bir editör denenmelidir. Dış komutları başlatmak zorunda olmayan daha genel düzenleme kancaları eklemek mümkündür; bu, geri çağrıyı doğrudan `EDITOR_CALLBACKS` vektörüne iterek yapılabilir.

`pattern` argümanı bir dize, düzenli ifade veya dize ve düzenli ifadelerden oluşan bir dizi olabilir. `fn`'nin çağrılması için, desenlerden biri `EDITOR`, `VISUAL` veya `JULIA_EDITOR` değerine uymalıdır. Dizeler için, dize, editör komutunun ilk kelimesinin [`basename`](@ref) ile eşleşmeli ve uzantısı, varsa, kaldırılmalıdır. Örneğin, "vi" "vim -g" ile eşleşmez, ancak "/usr/bin/vi -m" ile eşleşir; ayrıca `vi.exe` ile de eşleşir. Eğer `pattern` bir regex ise, tüm editör komutu, bir shell-escape edilmiş dize olarak karşılaştırılır. Bir dizi deseni, öğelerinden herhangi biri eşleşirse eşleşir. Birden fazla editör eşleşirse, en son eklenen kullanılır.

Varsayılan olarak, julia editörün kapanmasını beklemez, arka planda çalıştırır. Ancak, editör terminal tabanlıysa, muhtemelen `wait=true` ayarlamak isteyeceksiniz ve julia editör kapanmadan önce bekleyecektir.

Editör ortam değişkenlerinden biri ayarlandığında, ancak hiçbir editör girişi buna uymadığında, varsayılan editör girişi çağrılır:

```
(cmd, path, line, column) -> `$cmd $path`
```

Birçok editörün zaten tanımlandığını unutmayın. Aşağıdaki tüm komutlar zaten çalışmalıdır:

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# Örnekler

Aşağıdaki, terminal tabanlı `emacs` kullanımını tanımlar:

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor` Julia 1.4'te tanıtıldı.

