```
connect(path::AbstractString) -> PipeEndpoint
```

Verbinden Sie mit dem benannten Pipe / UNIX-Domain-Socket unter `path`.

!!! note
    Die Pfadlänge unter Unix ist auf irgendwo zwischen 92 und 108 Bytes begrenzt (vgl. `man unix`).

