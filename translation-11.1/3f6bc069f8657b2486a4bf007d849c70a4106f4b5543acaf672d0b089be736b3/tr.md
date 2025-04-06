```
repr(x; context=nothing)
```

Herhangi bir değerden bir dize oluşturmak için [`show`](@ref) fonksiyonunu kullanmalısınız. `repr`'e yöntem eklememelisiniz; bunun yerine bir `show` yöntemi tanımlayın.

İsteğe bağlı anahtar argümanı `context`, bir `:key=>value` çifti, `:key=>value` çiftleri içeren bir demet veya `show`'a geçirilen I/O akışı için kullanılan özelliklere sahip bir `IO` veya [`IOContext`](@ref) nesnesi olarak ayarlanabilir.

`repr(x)`'in genellikle `x`'in Julia'da nasıl girileceğine benzer olduğunu unutmayın. Bunun yanı sıra, `x`'in insan tüketimi için tasarlanmış "güzel yazılmış" bir versiyonunu döndürmek için [`repr(MIME("text/plain"), x)`](@ref) kullanın; bu, `x`'in REPL görüntülemesine eşdeğerdir.

!!! compat "Julia 1.7"
    Anahtar `context`'e bir demet geçmek, Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```
