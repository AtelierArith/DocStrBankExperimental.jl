```
arg_read(f::Function, arg::ArgRead) -> f(arg_io)
```

`arg_read` fonksiyonu, aşağıdakilerden herhangi biri olabilen bir `arg` argümanını kabul eder:

  * `AbstractString`: okunmak üzere açılacak bir dosya yolu
  * `AbstractCmd`: standart çıktısından okunan bir komut
  * `IO`: okunacak açık bir IO tanıtıcısı

Gövde normal bir şekilde dönerse veya bir hata fırlatırsa, açılan bir yol `arg_read`'den dönerken kapatılacak ve bir `IO` tanıtıcısı `arg_read`'den dönerken boşaltılacak ancak kapatılmayacaktır.

Not: Bir dosya açıldığında, ArgTools `open(...)` çağrısına `lock = false` geçecektir. Bu nedenle, bu fonksiyondan dönen nesne birden fazla iş parçacığı tarafından kullanılmamalıdır. Bu kısıtlama gelecekte gevşetilebilir, bu da çalışan herhangi bir kodu bozmayacaktır.
