"     get*test*counts(::AbstractTestSet) -> TestCounts

Test setindeki her tür test sonucunun sayısını doğrudan sayan ve alt test setleri arasında toplamını hesaplayan özyinelemeli bir işlevdir.

Özel `AbstractTestSet`, toplamlarının `DefaultTestSet` ile birlikte sayılması ve görüntülenmesi için bu işlevi uygulamalıdır.

Eğer özel bir `TestSet` için bu uygulanmamışsa, yazdırma işlemi başarısızlıklar için `x` ve süre için `?s` raporlamaya geri döner."
