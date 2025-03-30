```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

Sabit boyutlu [`DenseVector{T}`](@ref DenseVector).

`kind` şu anda ya `:not_atomic` ya da `:atomic` olabilir. `:atomic`'in ne anlama geldiği hakkında daha fazla bilgi için [`AtomicMemory`](@ref) bölümüne bakın.

`addrspace` şu anda yalnızca Core.CPU olarak ayarlanabilir. Bu, GPU'lar gibi diğer sistemler tarafından genişletilmesine izin vermek için tasarlanmıştır; bu sistemler aşağıdaki gibi değerler tanımlayabilir:

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

Bu diğer addrspace'lerin tam anlamı, belirli arka uç tarafından tanımlanır, ancak kullanıcı CPU'da bunlara erişmeye çalışıyorsa hata verecektir.

!!! compat "Julia 1.11"
    Bu tür, Julia 1.11 veya daha yenisini gerektirir.

