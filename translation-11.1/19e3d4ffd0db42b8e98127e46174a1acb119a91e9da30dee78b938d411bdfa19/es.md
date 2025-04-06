El tipo `Header` es una estructura que representa los metadatos esenciales para un solo registro en un archivo tar con la siguiente definición:

```
struct Header
    path :: String # ruta relativa a la raíz
    type :: Symbol # indicador de tipo (ver abajo)
    mode :: UInt16 # modo/permisos (mejor visto en octal)
    size :: Int64  # tamaño de los datos del registro en bytes
    link :: String # ruta de destino de un enlace simbólico
end
```

Los tipos se representan con los siguientes símbolos: `file`, `hardlink`, `symlink`, `chardev`, `blockdev`, `directory`, `fifo`, o para tipos desconocidos, el carácter typeflag como símbolo. Tenga en cuenta que [`extract`](@ref) se niega a extraer tipos de registros que no sean `file`, `symlink` y `directory`; [`list`](@ref) solo enumerará otros tipos de registros si se llama con `strict=false`.

El formato tar incluye varios metadatos adicionales sobre los registros, incluidos los ID de usuario y grupo, los nombres de usuario y grupo, y las marcas de tiempo. El paquete `Tar`, por diseño, ignora completamente estos. Al crear archivos tar, estos campos siempre se establecen en cero/vacío. Al leer archivos tar, estos campos se ignoran aparte de verificar las sumas de verificación de los encabezados para cada registro de encabezado para todos los campos.
