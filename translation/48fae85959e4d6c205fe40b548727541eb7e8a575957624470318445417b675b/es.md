```
ssh_key_pass() :: String
```

La función `ssh_key_pass()` devuelve el valor de la variable de entorno `SSH_KEY_PASS` si está configurada o `nothing` si no está configurada. En el futuro, esto podría ser capaz de encontrar una contraseña por otros medios, como almacenamiento seguro del sistema, por lo que los paquetes que necesiten una contraseña para descifrar una clave privada SSH deberían usar esta API en lugar de verificar directamente la variable de entorno para que obtengan tales capacidades automáticamente cuando se añadan.
