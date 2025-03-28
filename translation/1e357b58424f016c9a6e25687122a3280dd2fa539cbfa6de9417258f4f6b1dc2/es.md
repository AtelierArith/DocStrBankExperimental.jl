```
yield(t::Task, arg = nothing)
```

Una versión rápida y de programación injusta de `schedule(t, arg); yield()` que cede inmediatamente a `t` antes de llamar al programador.
