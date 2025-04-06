```
@__DIR__ -> String
```

Macro para obtener la ruta absoluta del directorio actual como una cadena.

Si se encuentra en un script, devuelve el directorio del script que contiene la llamada a la macro `@__DIR__`. Si se ejecuta desde un REPL o si se evalúa con `julia -e <expr>`, devuelve el directorio de trabajo actual.

# Ejemplos

El ejemplo ilustra la diferencia en los comportamientos de `@__DIR__` y `pwd()`, creando un script simple en un directorio diferente al directorio de trabajo actual y ejecutando ambos comandos:

```julia-repl
julia> cd("/home/JuliaUser") # directorio de trabajo

julia> # crear script en /home/JuliaUser/Projects
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # salida del directorio del script y del directorio de trabajo actual
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
