```
@debug mensaje  [clave=valor | valor ...]
@info  mensaje  [clave=valor | valor ...]
@warn  mensaje  [clave=valor | valor ...]
@error mensaje  [clave=valor | valor ...]

@logmsg nivel mensaje [clave=valor | valor ...]
```

Crea un registro de log con un `mensaje` informativo. Para conveniencia, se definen cuatro macros de logging `@debug`, `@info`, `@warn` y `@error` que registran en los niveles de severidad estándar `Debug`, `Info`, `Warn` y `Error`. `@logmsg` permite que `nivel` se establezca programáticamente a cualquier `LogLevel` o tipos de niveles de log personalizados.

`mensaje` debe ser una expresión que evalúe a una cadena que sea una descripción legible por humanos del evento de log. Por convención, esta cadena se formateará como markdown cuando se presente.

La lista opcional de pares `clave=valor` admite metadatos arbitrarios definidos por el usuario que se pasarán al backend de logging como parte del registro de log. Si solo se proporciona una expresión `valor`, se generará una clave que representa la expresión utilizando [`Symbol`](@ref). Por ejemplo, `x` se convierte en `x=x`, y `foo(10)` se convierte en `Symbol("foo(10)")=foo(10)`. Para descomponer una lista de pares clave-valor, utiliza la sintaxis normal de descomposición, `@info "blah" kws...`.

Hay algunas claves que permiten anular datos de log generados automáticamente:

  * `_module=mod` se puede usar para especificar un módulo de origen diferente de la ubicación de origen del mensaje.
  * `_group=symbol` se puede usar para anular el grupo de mensajes (esto normalmente se deriva del nombre base del archivo de origen).
  * `_id=symbol` se puede usar para anular el identificador único de mensaje generado automáticamente. Esto es útil si necesitas asociar muy de cerca mensajes generados en diferentes líneas de origen.
  * `_file=string` y `_line=integer` se pueden usar para anular la aparente ubicación de origen de un mensaje de log.

También hay algunos pares clave-valor que tienen un significado convencional:

  * `maxlog=integer` debe usarse como una pista para el backend de que el mensaje no debe mostrarse más de `maxlog` veces.
  * `exception=ex` debe usarse para transportar una excepción con un mensaje de log, a menudo utilizado con `@error`. Un backtrace asociado `bt` puede adjuntarse utilizando la tupla `exception=(ex,bt)`.

# Ejemplos

```julia
@debug "Información de depuración detallada.  Invisible por defecto"
@info  "Un mensaje informativo"
@warn  "Algo fue extraño.  Deberías prestar atención"
@error "Ocurrió un error no fatal"

x = 10
@info "Algunas variables adjuntas al mensaje" x a=42.0

@debug begin
    sA = sum(A)
    "sum(A) = $sA es una operación costosa, evaluada solo cuando `shouldlog` devuelve verdadero"
end

for i=1:10000
    @info "Con el backend por defecto, solo verás (i = $i) diez veces"  maxlog=10
    @debug "Algoritmo1" i progress=i/10000
end
```
