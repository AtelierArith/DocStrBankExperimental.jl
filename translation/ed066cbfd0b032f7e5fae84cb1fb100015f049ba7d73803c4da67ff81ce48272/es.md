```
ssh_key_path() :: String
```

La función `ssh_key_path()` devuelve la ruta del archivo de clave privada SSH que debe usarse para las conexiones SSH. Si la variable de entorno `SSH_KEY_PATH` está configurada, entonces devolverá ese valor. De lo contrario, por defecto devolverá

```
joinpath(ssh_dir(), ssh_key_name())
```

Este valor por defecto, a su vez, depende de las variables de entorno `SSH_DIR` y `SSH_KEY_NAME`.
