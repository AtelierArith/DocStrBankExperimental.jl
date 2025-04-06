```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

Construye un objeto `GitBlame` para el archivo en `path`, utilizando información de cambios obtenida de la historia de `repo`. El objeto `GitBlame` registra quién cambió qué partes del archivo, cuándo y cómo. `options` controla cómo separar el contenido del archivo y qué commits investigar - consulta [`BlameOptions`](@ref) para más información.
