```
arg_write(f::Function, arg::ArgWrite) -> arg
arg_write(f::Function, arg::Nothing) -> tempname()
```

`arg_read` fonksiyonu, aşağıdakilerden herhangi biri olabilen bir `arg` argümanını kabul eder:

  * `AbstractString`: yazma için açılacak bir dosya yolu
  * `AbstractCmd`: standart girdi olarak yazma işlemi yapılacak bir komut
  * `IO`: yazma işlemi yapılacak açık bir IO tanıtıcısı
  * `Nothing`: yazma işlemi için geçici bir yol açılmalıdır

Eğer gövde normal bir şekilde dönerse, açılan bir yol tamamlandığında kapatılacaktır; bir IO tanıtıcısı argümanı açık bırakılır ancak dönüşten önce boşaltılır. Eğer argüman `nothing` ise, yazma işlemi için geçici bir yol açılır ve tamamlandığında kapatılır ve yol `arg_write` fonksiyonundan döner. Diğer tüm durumlarda, `arg` kendisi döner. Bu, bir argüman geçilip geçilmediğine bakılmaksızın yazılan her şeyi tutarlı bir şekilde döndürebilmeniz için yararlı bir modeldir.

Eğer gövdenin değerlendirilmesi sırasında bir hata olursa, `arg_write` tarafından yazma işlemi için açılan bir yol silinecektir; bu, bir dize olarak geçilmiş olsun ya da `arg` `nothing` olduğunda üretilen geçici bir yol olsun.

Not: Bir dosya açarken, ArgTools `open(...)` çağrısına `lock = false` parametresini geçecektir. Bu nedenle, bu fonksiyondan dönen nesne birden fazla iş parçacığı tarafından kullanılmamalıdır. Bu kısıtlama gelecekte gevşetilebilir, bu da çalışan herhangi bir kodu bozmaz.
