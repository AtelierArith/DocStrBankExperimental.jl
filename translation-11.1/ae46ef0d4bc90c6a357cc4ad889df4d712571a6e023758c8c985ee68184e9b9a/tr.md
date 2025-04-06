```
makro artifact_str(isim)
```

Diskteki bir artefaktın yolunu döndürür. Artefaktı projenin `(Julia)Artifacts.toml` dosyasında isme göre otomatik olarak arar. İstenen artefakt mevcut değilse bir hata fırlatır. REPL'de çalıştırıldığında, toml dosyasını mevcut dizinden başlayarak arar, daha fazla bilgi için `find_artifacts_toml()`'a bakın.

Eğer artefakt "tembel" olarak işaretlenmişse ve paket `using LazyArtifacts` tanımlıysa, bu makro ilk kez yolu hesaplamaya çalıştığında artefakt talep üzerine `Pkg` ile indirilecektir. Dosyalar daha sonra yerel olarak kurulu bırakılacaktır.

Eğer `isim` bir ileri veya geri eğik çizgi içeriyorsa, ilk eğik çizgiden sonraki tüm öğeler artefakta dizinleme yapan yol adları olarak alınacaktır, bu da bir artefakt içindeki tek bir dosya/dizin erişimi için kolay bir tek satırlık çözüm sağlar. Örnek:

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! uyumluluk "Julia 1.3"
    Bu makro en az Julia 1.3 gerektirir.


!!! uyumluluk "Julia 1.6"
    Eğik çizgi dizinleme en az Julia 1.6 gerektirir.

