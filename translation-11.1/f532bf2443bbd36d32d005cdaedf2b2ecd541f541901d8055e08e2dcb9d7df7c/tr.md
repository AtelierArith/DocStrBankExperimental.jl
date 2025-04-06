[`Threads.Condition`](@ref) için özel not:

Çağrıcı, bu yöntemi çağırmadan önce bir `Threads.Condition`'a sahip olan [`lock`](@ref) tutmalıdır. Çağrılan görev, genellikle aynı `Threads.Condition` nesnesi üzerinde [`notify`](@ref) çağrılarak başka bir görev tarafından uyandırılana kadar engellenecektir. Engelleme sırasında kilit atomik olarak serbest bırakılacak (kendi kendine kilitlenmiş olsa bile) ve geri dönerken yeniden edinilecektir.
