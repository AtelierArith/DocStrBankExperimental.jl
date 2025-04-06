```
close(c::Channel[, excp::Exception])
```

Schließt einen Kanal. Eine Ausnahme (optional angegeben durch `excp`) wird ausgelöst durch:

  * [`put!`](@ref) auf einem geschlossenen Kanal.
  * [`take!`](@ref) und [`fetch`](@ref) auf einem leeren, geschlossenen Kanal.
