```
@elapsed
```

Bir ifadeyi değerlendirmek için bir makro, sonuç değerini atlayarak, yerine yürütmenin kaç saniye sürdüğünü kayan nokta sayısı olarak döndürür.

Bazı durumlarda sistem `@elapsed` ifadesinin içine bakacak ve üst düzey ifadenin yürütülmesi başlamadan önce çağrılan kodun bir kısmını derleyecektir. Bu olduğunda, bazı derleme süreleri sayılmayacaktır. Bu süreyi dahil etmek için `@elapsed @eval ...` komutunu çalıştırabilirsiniz.

Ayrıca [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@allocated`](@ref) ve [`@allocations`](@ref) ile de bakabilirsiniz.

```julia-repl
julia> @elapsed sleep(0.3)
0.301391426
```
