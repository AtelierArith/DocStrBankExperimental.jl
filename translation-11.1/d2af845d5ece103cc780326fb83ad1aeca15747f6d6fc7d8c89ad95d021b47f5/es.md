```
Pipe()
```

Construye un objeto Pipe no inicializado, especialmente para la comunicación de IO entre múltiples procesos.

El extremo apropiado del pipe se inicializará automáticamente si el objeto se utiliza en la creación de procesos. Esto puede ser útil para obtener fácilmente referencias en tuberías de procesos, por ejemplo:

```
julia> err = Pipe()

# Después de esto, `err` estará inicializado y podrás leer `foo`'s
# stderr desde el pipe `err`, o pasar `err` a otras tuberías.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# Ahora destruye la mitad de escritura del pipe, para que la mitad de lectura obtenga EOF
julia> closewrite(err)

julia> read(err, String)
"stderr messages"
```

Consulta también [`Base.link_pipe!`](@ref).
