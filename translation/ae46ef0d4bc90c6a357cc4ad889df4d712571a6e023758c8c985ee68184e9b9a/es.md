```
macro artifact_str(name)
```

Devuelve la ruta en disco a un artefacto. Busca automáticamente el artefacto por nombre en el archivo `(Julia)Artifacts.toml` del proyecto. Lanza un error si el artefacto solicitado no está presente. Si se ejecuta en el REPL, busca el archivo toml comenzando en el directorio actual, consulta `find_artifacts_toml()` para más información.

Si el artefacto está marcado como "perezoso" y el paquete tiene `using LazyArtifacts` definido, el artefacto se descargará bajo demanda con `Pkg` la primera vez que esta macro intente calcular la ruta. Los archivos se dejarán instalados localmente para su uso posterior.

Si `name` contiene una barra diagonal hacia adelante o hacia atrás, todos los elementos después de la primera barra se tomarán como nombres de ruta que indexan en el artefacto, lo que permite una línea fácil para acceder a un solo archivo/directorio dentro de un artefacto. Ejemplo:

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! compat "Julia 1.3"
    Esta macro requiere al menos Julia 1.3.


!!! compat "Julia 1.6"
    La indexación con barra requiere al menos Julia 1.6.

