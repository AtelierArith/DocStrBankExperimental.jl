```
getglobal(module::Module, name::Symbol, [order::Symbol=:monotonic])
```

`module`'dan `name` bağlamasının değerini alır. İsteğe bağlı olarak, işlem için atomik bir sıralama tanımlanabilir, aksi takdirde varsayılan olarak monotonik olur.

Modül bağlamalarına [`getfield`](@ref) kullanarak erişim sağlamak hala desteklenmektedir, ancak `getglobal` kullanmak her zaman tercih edilmelidir çünkü `getglobal` atomik sıralama üzerinde kontrol sağlar (`getfield` her zaman monotoniktir) ve kodun niyetini hem kullanıcıya hem de derleyiciye daha iyi belirtir.

Çoğu kullanıcı bu işlevi doğrudan çağırmak zorunda kalmamalıdır – [`getproperty`](@ref Base.getproperty) işlevi veya karşılık gelen sözdizimi (yani `module.name`) çok az özel kullanım durumu dışında tercih edilmelidir.

!!! compat "Julia 1.9"
    Bu işlev Julia 1.9 veya daha yenisini gerektirir.


Ayrıca bkz. [`getproperty`](@ref Base.getproperty) ve [`setglobal!`](@ref).

# Örnekler

```jldoctest
julia> a = 1
1

julia> module M
       a = 2
       end;

julia> getglobal(@__MODULE__, :a)
1

julia> getglobal(M, :a)
2
```
