```
tempdir()
```

Obtiene la ruta del directorio temporal. En Windows, `tempdir()` utiliza la primera variable de entorno encontrada en la lista ordenada `TMP`, `TEMP`, `USERPROFILE`. En todos los demás sistemas operativos, `tempdir()` utiliza la primera variable de entorno encontrada en la lista ordenada `TMPDIR`, `TMP`, `TEMP` y `TEMPDIR`. Si ninguna de estas se encuentra, se utiliza la ruta `"/tmp"`.
