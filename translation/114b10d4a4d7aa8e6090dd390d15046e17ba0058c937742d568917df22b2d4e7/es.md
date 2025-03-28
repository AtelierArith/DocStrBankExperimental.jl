```
catch_exceptions(logger)
```

Devuelve `true` si el registrador debe capturar excepciones que ocurren durante la construcción del registro de log. Por defecto, los mensajes son capturados.

Por defecto, todas las excepciones son capturadas para evitar que la generación de mensajes de log haga que el programa se bloquee. Esto permite a los usuarios activar con confianza funcionalidades poco utilizadas, como el registro de depuración, en un sistema de producción.

Si deseas utilizar el registro como un rastro de auditoría, deberías desactivar esto para tu tipo de registrador.
