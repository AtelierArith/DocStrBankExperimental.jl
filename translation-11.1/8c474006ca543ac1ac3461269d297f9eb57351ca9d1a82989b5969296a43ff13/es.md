```
ssh_known_hosts_file() :: String
```

La función `ssh_known_hosts_file()` devuelve una única ruta de un archivo de hosts conocidos de SSH que debe utilizarse al establecer las identidades de los servidores remotos para conexiones SSH. Devuelve la primera ruta devuelta por `ssh_known_hosts_files` que realmente existe. Los llamadores que pueden buscar en más de un archivo de hosts conocidos deben usar `ssh_known_hosts_files` en su lugar y buscar coincidencias de hosts en todos los archivos devueltos, como se describe en la documentación de esa función.
