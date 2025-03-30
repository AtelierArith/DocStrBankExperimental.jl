```
pipeline(command; stdin, stdout, stderr, append=false)
```

Verilen `command`'a I/O yönlendirin. Anahtar kelime argümanları, komutun hangi akışlarının yönlendirileceğini belirtir. `append`, dosya çıktısının dosyaya eklenip eklenmeyeceğini kontrol eder. Bu, 2-argümanlı `pipeline` fonksiyonunun daha genel bir versiyonudur. `pipeline(from, to)` bir komut olduğunda `pipeline(from, stdout=to)` ile eşdeğerdir ve `from` başka bir veri kaynağı olduğunda `pipeline(to, stdin=from)` ile eşdeğerdir.

**Örnekler**:

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
