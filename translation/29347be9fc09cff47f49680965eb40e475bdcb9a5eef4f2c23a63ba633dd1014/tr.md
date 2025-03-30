`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle` bir `AbstractArray` türü ile ilişkili herhangi bir stil için soyut süper türdür. `N` parametresi, belirli boyutları yalnızca destekleyen `AbstractArray` türleri için kullanışlı olabilecek boyutsallığı temsil eder:

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

Herhangi bir boyutsallığı destekleyen `AbstractArray` türleri için, `N` `Any` olarak ayarlanabilir:

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

Birden fazla `AbstractArrayStyle`'ı karıştırabilmek ve boyutsallığı takip edebilmek istediğiniz durumlarda, stilinizin bir [`Val`](@ref) yapıcıyı desteklemesi gerekir:

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

İki veya daha fazla `AbstractArrayStyle` alt türü çelişirse, yayılma mekanizması `Array` üretmeye geri dönecektir. Bu istenmiyorsa, çıktı türünü kontrol etmek için ikili [`BroadcastStyle`](@ref) kuralları tanımlamanız gerekebilir.

Ayrıca [`Broadcast.DefaultArrayStyle`](@ref) ile de bakabilirsiniz.
