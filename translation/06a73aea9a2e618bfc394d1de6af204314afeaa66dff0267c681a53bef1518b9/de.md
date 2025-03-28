```
listen(path::AbstractString) -> PipeServer
```

Erstellen und auf einem benannten Pipe / UNIX-Domain-Socket hören.

!!! note
    Die Pfadlänge unter Unix ist auf irgendwo zwischen 92 und 108 Bytes begrenzt (vgl. `man unix`).

