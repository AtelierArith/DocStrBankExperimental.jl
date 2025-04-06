```
Threads.Condition([lock])
```

Une version thread-safe de [`Base.Condition`](@ref).

Pour appeler [`wait`](@ref) ou [`notify`](@ref) sur un `Threads.Condition`, vous devez d'abord appeler [`lock`](@ref) dessus. Lorsque `wait` est appelé, le verrou est libéré de manière atomique pendant le blocage, et sera réacquis avant que `wait` ne retourne. Par conséquent, l'utilisation idiomatique d'un `Threads.Condition` `c` ressemble à ce qui suit :

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    Cette fonctionnalité nécessite au moins Julia 1.2.

