```
macroexpand(m::Module, x; recursive=true)
```

Toma la expresión `x` y devuelve una expresión equivalente con todas las macros eliminadas (expandidas) para ejecutarse en el módulo `m`. La palabra clave `recursive` controla si también se expanden niveles más profundos de macros anidadas. Esto se demuestra en el ejemplo a continuación:

```julia-repl
julia> module M
           macro m1()
               42
           end
           macro m2()
               :(@m1())
           end
       end
M

julia> macroexpand(M, :(@m2()), recursive=true)
42

julia> macroexpand(M, :(@m2()), recursive=false)
:(#= REPL[16]:6 =# M.@m1)
```
