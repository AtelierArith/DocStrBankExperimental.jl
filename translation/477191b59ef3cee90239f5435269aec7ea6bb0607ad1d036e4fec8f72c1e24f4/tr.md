```
macroexpand(m::Module, x; recursive=true)
```

Verilen `x` ifadesini alır ve `m` modülünde çalıştırmak için tüm makroları kaldırılmış (genişletilmiş) eşdeğer bir ifade döndürür. `recursive` anahtar kelimesi, daha derin seviyelerdeki iç içe makroların da genişletilip genişletilmeyeceğini kontrol eder. Bu, aşağıdaki örnekte gösterilmiştir:

```julia-repl
julia> module M
           macro m1()
               42
           end
           macro m2()
               :(@m1())
           end
       end
M

julia> macroexpand(M, :(@m2()), recursive=true)
42

julia> macroexpand(M, :(@m2()), recursive=false)
:(#= REPL[16]:6 =# M.@m1)
```
