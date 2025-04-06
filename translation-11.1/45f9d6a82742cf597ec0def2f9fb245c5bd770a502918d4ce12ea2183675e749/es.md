```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

Empuja al repositorio remoto git `rmt` especificado, utilizando `refspecs` para determinar a qué rama(s) remota(s) empujar. Los argumentos de palabra clave son:

  * `force`: si es `true`, se realizará un empuje forzado, ignorando los conflictos.
  * `options`: determina las opciones para el empuje, por ejemplo, qué encabezados de proxy usar. Consulta [`PushOptions`](@ref) para más información.

!!! note
    Puedes agregar información sobre los refspecs de empuje de dos maneras adicionales: configurando una opción en el `GitConfig` del repositorio (con `push.default` como clave) o llamando a [`add_push!`](@ref). De lo contrario, necesitarás especificar explícitamente un refspec de empuje en la llamada a `push` para que tenga algún efecto, así: `LibGit2.push(repo, refspecs=["refs/heads/master"])`.

