```
stat(file)
```

Devuelve una estructura cuyos campos contienen información sobre el archivo. Los campos de la estructura son:

| Nombre  | Tipo                            | Descripción                                                                          |
|:------- |:------------------------------- |:------------------------------------------------------------------------------------ |
| desc    | `Union{String, Base.OS_HANDLE}` | La ruta o descriptor de archivo del sistema operativo                                |
| size    | `Int64`                         | El tamaño (en bytes) del archivo                                                     |
| device  | `UInt`                          | ID del dispositivo que contiene el archivo                                           |
| inode   | `UInt`                          | El número de inode del archivo                                                       |
| mode    | `UInt`                          | El modo de protección del archivo                                                    |
| nlink   | `Int`                           | El número de enlaces duros al archivo                                                |
| uid     | `UInt`                          | El id de usuario del propietario del archivo                                         |
| gid     | `UInt`                          | El id de grupo del propietario del archivo                                           |
| rdev    | `UInt`                          | Si este archivo se refiere a un dispositivo, el ID del dispositivo al que se refiere |
| blksize | `Int64`                         | El tamaño de bloque preferido del sistema de archivos para el archivo                |
| blocks  | `Int64`                         | El número de bloques de 512 bytes asignados                                          |
| mtime   | `Float64`                       | Marca de tiempo Unix de cuándo fue modificado por última vez el archivo              |
| ctime   | `Float64`                       | Marca de tiempo Unix de cuándo se cambió la metadata del archivo                     |
