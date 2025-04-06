```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

Bir `AbstractTestSet`'in sonuçlarını biçimlendirilmiş bir tablo olarak yazdırır.

`depth_pad`, tüm çıktının önüne ne kadar boşluk eklenmesi gerektiğini belirtir.

`Test.finish` içinde çağrılır, eğer `finish` edilen test seti en üstteki test setiyse.
