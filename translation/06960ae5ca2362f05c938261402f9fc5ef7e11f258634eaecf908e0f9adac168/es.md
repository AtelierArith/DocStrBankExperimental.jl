```
setenv(command::Cmd, env; dir)
```

Establece las variables de entorno que se utilizarán al ejecutar el `command` dado. `env` es un diccionario que mapea cadenas a cadenas, un arreglo de cadenas de la forma `"var=val"`, o cero o más argumentos de pares `"var"=>val`. Para modificar (en lugar de reemplazar) el entorno existente, crea `env` a través de `copy(ENV)` y luego establece `env["var"]=val` según sea necesario, o usa [`addenv`](@ref).

El argumento clave `dir` se puede usar para especificar un directorio de trabajo para el comando. `dir` por defecto es el `dir` actualmente establecido para `command` (que es el directorio de trabajo actual si no se especifica ya).

Consulta también [`Cmd`](@ref), [`addenv`](@ref), [`ENV`](@ref), [`pwd`](@ref).
