```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

Crea una nueva tarea a partir de `func`, la vincula a un nuevo canal de tipo `T` y tamaño `size`, y programa la tarea, todo en una sola llamada. El canal se cierra automáticamente cuando la tarea termina.

`func` debe aceptar el canal vinculado como su único argumento.

Si necesitas una referencia a la tarea creada, pasa un objeto `Ref{Task}` a través del argumento de palabra clave `taskref`.

Si `spawn=true`, la `Task` creada para `func` puede ser programada en otro hilo en paralelo, equivalente a crear una tarea a través de [`Threads.@spawn`](@ref).

Si `spawn=true` y el argumento `threadpool` no está establecido, por defecto es `:default`.

Si el argumento `threadpool` está establecido (a `:default` o `:interactive`), esto implica que `spawn=true` y la nueva Task se genera en el threadpool especificado.

Devuelve un `Channel`.

# Ejemplos

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

Referenciando la tarea creada:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    El parámetro `spawn=` se agregó en Julia 1.3. Este constructor se agregó en Julia 1.3. En versiones anteriores de Julia, Channel utilizaba argumentos de palabra clave para establecer `size` y `T`, pero esos constructores están en desuso.


!!! compat "Julia 1.9"
    El argumento `threadpool=` se agregó en Julia 1.9.


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```
