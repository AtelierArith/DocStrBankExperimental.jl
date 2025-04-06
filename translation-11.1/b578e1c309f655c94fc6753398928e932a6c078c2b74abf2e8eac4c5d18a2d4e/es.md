```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

Obtiene del repositorio remoto git `rmt` especificado, utilizando `refspecs` para determinar qué rama(s) remota(s) obtener. Los argumentos de palabra clave son:

  * `options`: determina las opciones para la obtención, por ejemplo, si se debe podar después. Consulta [`FetchOptions`](@ref) para más información.
  * `msg`: un mensaje para insertar en los reflogs.
