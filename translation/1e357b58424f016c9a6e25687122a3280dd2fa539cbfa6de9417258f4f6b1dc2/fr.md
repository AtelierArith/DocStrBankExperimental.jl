```
yield(t::Task, arg = nothing)
```

Une version rapide et de planification injuste de `schedule(t, arg); yield()` qui cède immédiatement à `t` avant d'appeler le planificateur.
