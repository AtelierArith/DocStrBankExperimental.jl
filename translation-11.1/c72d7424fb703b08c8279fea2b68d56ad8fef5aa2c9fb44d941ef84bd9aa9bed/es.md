# macOS

Necesitas tener instaladas las utilidades de línea de comandos de Xcode: ejecuta `xcode-select --install` en la terminal. Necesitarás volver a ejecutar este comando de terminal después de cada actualización de macOS, de lo contrario, podrías encontrarte con errores relacionados con bibliotecas o encabezados faltantes.

Las bibliotecas dependientes ahora se construyen con [BinaryBuilder](https://binarybuilder.org) y se descargarán automáticamente. Esta es la forma preferida de construir el código fuente de Julia. En caso de que desees construirlas todas por tu cuenta, necesitarás un gfortran de 64 bits para compilar las dependencias de Julia.

```bash
brew install gcc
```

Si has configurado `LD_LIBRARY_PATH` o `DYLD_LIBRARY_PATH` en tu `.bashrc` o equivalente, Julia puede no ser capaz de encontrar varias bibliotecas que vienen incluidas con ella. Estas variables de entorno deben ser desactivadas para que Julia funcione.
