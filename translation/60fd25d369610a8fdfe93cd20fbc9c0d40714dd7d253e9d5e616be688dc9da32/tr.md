```
@cfunction(callable, ReturnType, (ArgumentTypes...,)) -> Ptr{Cvoid}
@cfunction($callable, ReturnType, (ArgumentTypes...,)) -> CFunction
```

Julia fonksiyonu `callable`'dan verilen tür imzası için C çağrılabilir bir fonksiyon işaretçisi oluşturun. Dönüş değerini bir `ccall`'e iletmek için, imzada `Ptr{Cvoid}` argüman türünü kullanın.

Argüman türü demetinin bir literal demet olması gerektiğini ve bir demet-değerli değişken veya ifade olmaması gerektiğini unutmayın (ancak bir splat ifadesi içerebilir). Ve bu argümanlar derleme zamanında global kapsamda değerlendirilecektir (çalışma zamanında ertelenmeyecek). Fonksiyon argümanının önüne bir '$' eklemek, bunun yerine yerel değişken `callable` üzerinde bir çalışma zamanı kapanışı oluşturur (bu tüm mimarilerde desteklenmez).

[ccall ve cfunction kullanımı hakkında kılavuz bölümü](@ref Calling-C-and-Fortran-Code) bölümüne bakın.

# Örnekler

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```
