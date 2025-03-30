```
rmprocs(pids...; waitfor=typemax(Int))
```

Belirtilen işçileri kaldırın. Sadece işlem 1'in işçi ekleyip kaldırabileceğini unutmayın.

`waitfor` argümanı, işçilerin kapanması için ne kadar süre bekleyeceğinizi belirtir:

  * Belirtilmemişse, `rmprocs` istenen tüm `pids` kaldırılana kadar bekleyecektir.
  * İstenilen `waitfor` saniyesinden önce tüm işçiler sonlandırılamazsa bir [`ErrorException`](@ref) hatası oluşur.
  * `waitfor` değeri 0 olduğunda, çağrı hemen döner ve işçilerin kaldırılması farklı bir görevde planlanır. Planlanan [`Task`](@ref) nesnesi döner. Kullanıcı, başka herhangi bir paralel çağrı yapmadan önce görev üzerinde [`wait`](@ref) çağrısı yapmalıdır.

# Örnekler

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```
