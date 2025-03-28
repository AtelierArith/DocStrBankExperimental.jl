```
ssh_pub_key_path() :: String
```

La función `ssh_pub_key_path()` devuelve la ruta del archivo de clave pública SSH que debe usarse para las conexiones SSH. Si la variable de entorno `SSH_PUB_KEY_PATH` está establecida, entonces devolverá ese valor. Si no está establecida pero `SSH_KEY_PATH` está configurada, devolverá esa ruta con el sufijo `.pub` añadido. Si ninguna de las dos está establecida, por defecto devolverá

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

Este valor por defecto, a su vez, depende de las variables de entorno `SSH_DIR` y `SSH_KEY_NAME`.
