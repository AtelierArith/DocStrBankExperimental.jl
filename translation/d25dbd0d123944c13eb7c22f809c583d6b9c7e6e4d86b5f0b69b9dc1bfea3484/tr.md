```
@everywhere [procs()] expr
```

Tüm `procs` üzerinde `Main` altında bir ifadeyi çalıştırın. Herhangi bir süreçteki hatalar, bir [`CompositeException`](@ref) içinde toplanır ve fırlatılır. Örneğin:

```
@everywhere bar = 1
```

tüm mevcut süreçlerde `Main.bar` tanımlayacaktır. Daha sonra eklenen süreçler (örneğin [`addprocs()`](@ref) ile) ifadenin tanımlı olmayacaktır.

[`@spawnat`](@ref) ile karşılaştırıldığında, `@everywhere` herhangi bir yerel değişkeni yakalamaz. Bunun yerine, yerel değişkenler interpolasyon kullanılarak yayılabilir:

```
foo = 1
@everywhere bar = $foo
```

İsteğe bağlı `procs` argümanı, ifadenin çalıştırılacağı tüm süreçlerin bir alt kümesini belirtmeye olanak tanır.

`remotecall_eval(Main, procs, expr)` çağrısına benzer, ancak iki ek özelliği vardır:

```
- `using` ve `import` ifadeleri önce çağıran süreçte çalıştırılır, böylece
  paketlerin önceden derlenmesi sağlanır.
- `include` tarafından kullanılan mevcut kaynak dosya yolu diğer süreçlere iletilir.
```
