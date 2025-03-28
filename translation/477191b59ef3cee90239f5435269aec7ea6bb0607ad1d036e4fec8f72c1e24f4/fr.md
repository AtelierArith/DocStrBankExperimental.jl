```
macroexpand(m::Module, x; recursive=true)
```

Prenez l'expression `x` et renvoyez une expression équivalente avec tous les macros supprimés (développés) pour l'exécution dans le module `m`. Le mot-clé `recursive` contrôle si des niveaux plus profonds de macros imbriquées sont également développés. Cela est démontré dans l'exemple ci-dessous :

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
