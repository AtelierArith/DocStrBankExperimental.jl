```
setglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Modül `module` içindeki `name` bağlamasının değerini `x` olarak ayarlayın veya değiştirin. Herhangi bir tür dönüşümü yapılmaz, bu nedenle bağlama için zaten bir tür tanımlandıysa, `x` uygun türde olmalıdır veya bir hata fırlatılır.

Ayrıca, bu işlem için atomik bir sıralama belirtilebilir, aksi takdirde varsayılan olarak monotonik olur.

Kullanıcılar genellikle bu işlevselliğe [`setproperty!`](@ref Base.setproperty!) fonksiyonu veya karşılık gelen sözdizimi (yani `module.name = x`) aracılığıyla erişecektir, bu nedenle bu yalnızca çok özel kullanım durumları için tasarlanmıştır.

!!! compat "Julia 1.9"
    Bu fonksiyon Julia 1.9 veya daha yenisini gerektirir.


Ayrıca bkz. [`setproperty!`](@ref Base.setproperty!) ve [`getglobal`](@ref)

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> module M; global a; end;

julia> M.a  # `getglobal(M, :a)` ile aynı
HATA: UndefVarError: `a` M içinde tanımlı değil
Öneri: uygun bir içe aktarma veya atama ekleyin. Bu global tanımlandı ama atanmadı.
Stacktrace:
 [1] getproperty(x::Module, f::Symbol)
   @ Base ./Base.jl:42
 [2] üst düzey kapsam
   @ none:1

julia> setglobal!(M, :a, 1)
1

julia> M.a
1
```
