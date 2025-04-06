```
close(c::Channel[, excp::Exception])
```

Bir kanalı kapat. Bir istisna (isteğe bağlı olarak `excp` ile verilen) aşağıdakilerden biri tarafından fırlatılır:

  * [`put!`](@ref) kapalı bir kanalda.
  * [`take!`](@ref) ve [`fetch`](@ref) boş, kapalı bir kanalda.
