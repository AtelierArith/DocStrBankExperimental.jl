```
@macroexpand [mod,] ex
```

Tüm makrolar kaldırılarak (genişletilerek) eşdeğer ifade döndürülür. İki argüman sağlandığında, ilki değerlendirilecek modüldür.

`@macroexpand` ve [`macroexpand`](@ref) arasında farklılıklar vardır.

  * [`macroexpand`](@ref) bir anahtar kelime argümanı `recursive` alırken, `@macroexpand` her zaman rekursiftir. Rekursif olmayan bir makro versiyonu için [`@macroexpand1`](@ref) bakın.
  * [`macroexpand`](@ref) açık bir `module` argümanına sahipken, `@macroexpand` her zaman çağrıldığı modüle göre genişletir.

Bu en iyi aşağıdaki örnekte görülmektedir:

```julia-repl
julia> module M
           macro m()
               1
           end
           function f()
               (@macroexpand(@m),
                macroexpand(M, :(@m)),
                macroexpand(Main, :(@m))
               )
           end
       end
M

julia> macro m()
           2
       end
@m (1 yöntemli makro)

julia> M.f()
(1, 1, 2)
```

`@macroexpand` ile ifade, kodda `@macroexpand`'in göründüğü yerde genişletilir (örnekte modül `M`). `macroexpand` ile ifade, ilk argüman olarak verilen modülde genişletilir.

!!! compat "Julia 1.11"
    İki argümanlı form en az Julia 1.11 gerektirir.

