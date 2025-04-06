```
@sync
```

Tüm sözdizimsel olarak kapsanan [`@async`](@ref), [`@spawn`](@ref Threads.@spawn), `Distributed.@spawnat` ve `Distributed.@distributed` kullanımlarının tamamlanmasını bekleyin. Kapsanan asenkron işlemler tarafından fırlatılan tüm istisnalar toplanır ve bir [`CompositeException`](@ref) olarak fırlatılır.

# Örnekler

```julia-repl
julia> Threads.nthreads()
4

julia> @sync begin
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 1")
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 2")
       end;
Thread-id 3, task 1
Thread-id 1, task 2
```
