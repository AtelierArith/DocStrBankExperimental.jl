```
ssh_key_name() :: String
```

La función `ssh_key_name()` devuelve el nombre base de los archivos de clave que SSH debería usar al establecer una conexión. Por lo general, no hay razón para que esta función se llame directamente y las bibliotecas deberían usar generalmente las funciones `ssh_key_path` y `ssh_pub_key_path` para obtener rutas completas. Si la variable de entorno `SSH_KEY_NAME` está establecida, entonces esta función devuelve eso; de lo contrario, devuelve `id_rsa` por defecto.
