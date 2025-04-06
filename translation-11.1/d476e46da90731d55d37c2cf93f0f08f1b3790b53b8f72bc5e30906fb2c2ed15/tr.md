```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

`tests` içinde listelenen Julia birim testlerini çalıştırın; bu, bir dize veya dizeler dizisi olabilir ve `ncores` işlemcisi kullanır. `exit_on_error` `false` ise, bir test başarısız olduğunda, diğer dosyalardaki tüm kalan testler yine de çalıştırılacaktır; aksi takdirde, `exit_on_error == true` olduğunda atlanır. `revise` `true` ise, testler çalıştırılmadan önce `Base` veya standart kütüphanelerdeki herhangi bir değişikliği yüklemek için `Revise` paketi kullanılır. Eğer bir tohum anahtar argümanı aracılığıyla sağlanmışsa, bu, testlerin çalıştırıldığı bağlamda küresel RNG'yi tohumlamak için kullanılır; aksi takdirde tohum rastgele seçilir.
