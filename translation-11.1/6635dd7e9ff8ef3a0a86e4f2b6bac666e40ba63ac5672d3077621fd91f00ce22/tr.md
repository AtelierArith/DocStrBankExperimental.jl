Unsafe pointer işlemleri, C11 ve C++23'te sırasıyla `_Atomic` ve `std::atomic` türü ile tanımlanmış işaretçilerin yüklenmesi ve saklanması ile uyumludur. Julia türü `T` için atomik yükleme desteği yoksa bir hata fırlatılabilir.

Ayrıca bakınız: [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
