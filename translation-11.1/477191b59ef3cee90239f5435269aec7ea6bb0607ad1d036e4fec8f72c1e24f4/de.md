```
macroexpand(m::Module, x; recursive=true)
```

Nehmen Sie den Ausdruck `x` und geben Sie einen äquivalenten Ausdruck zurück, bei dem alle Makros entfernt (erweitert) wurden, um in Modul `m` ausgeführt zu werden. Das Schlüsselwort `recursive` steuert, ob auch tiefere Ebenen von geschachtelten Makros erweitert werden. Dies wird im folgenden Beispiel demonstriert:

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
