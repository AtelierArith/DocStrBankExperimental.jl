```
@timed
```

Bir ifadeyi yürütmek ve ifadenin değerini, geçen süreyi saniye cinsinden, toplam tahsis edilen baytları, çöp toplama süresini, çeşitli bellek tahsis sayıcılarıyla bir nesneyi, derleme süresini saniye cinsinden ve yeniden derleme süresini saniye cinsinden döndüren bir makro. Bir [`ReentrantLock`](@ref) beklemek zorunda kaldığında herhangi bir kilit çatışması sayısı olarak gösterilir.

Bazı durumlarda sistem, `@timed` ifadesinin içine bakacak ve üst düzey ifadenin yürütülmesi başlamadan önce çağrılan kodun bir kısmını derleyecektir. Bu olduğunda, bazı derleme süreleri sayılmayacaktır. Bu süreyi dahil etmek için `@timed @eval ...` komutunu çalıştırabilirsiniz.

Ayrıca [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), [`@allocations`](@ref) ve [`@lock_conflicts`](@ref) ile de bakabilirsiniz.

```julia-repl
julia> stats = @timed rand(10^6);

julia> stats.time
0.006634834

julia> stats.bytes
8000256

julia> stats.gctime
0.0055765

julia> propertynames(stats.gcstats)
(:allocd, :malloc, :realloc, :poolalloc, :bigalloc, :freecall, :total_time, :pause, :full_sweep)

julia> stats.gcstats.total_time
5576500

julia> stats.compile_time
0.0

julia> stats.recompile_time
0.0

```

!!! compat "Julia 1.5"
    Bu makronun dönüş tipi Julia 1.5'te `Tuple`'dan `NamedTuple`'a değiştirildi.


!!! compat "Julia 1.11"
    `lock_conflicts`, `compile_time` ve `recompile_time` alanları Julia 1.11'de eklendi.

