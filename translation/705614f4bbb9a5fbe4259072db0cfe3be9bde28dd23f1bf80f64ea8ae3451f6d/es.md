```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

Lee una matriz de la fuente donde cada línea (separada por `eol`) da una fila, con elementos separados por el delimitador dado. La fuente puede ser un archivo de texto, un flujo o un arreglo de bytes. Se pueden usar archivos mapeados en memoria pasando la representación del arreglo de bytes del segmento mapeado como fuente.

Si `T` es un tipo numérico, el resultado es un arreglo de ese tipo, con cualquier elemento no numérico como `NaN` para tipos de punto flotante, o cero. Otros valores útiles de `T` incluyen `String`, `AbstractString` y `Any`.

Si `header` es `true`, la primera fila de datos se leerá como encabezado y se devolverá la tupla `(data_cells, header_cells)` en lugar de solo `data_cells`.

Especificar `skipstart` ignorará el número correspondiente de líneas iniciales de la entrada.

Si `skipblanks` es `true`, las líneas en blanco en la entrada serán ignoradas.

Si `use_mmap` es `true`, el archivo especificado por `source` se mapea en memoria para posibles aceleraciones si el archivo es grande. El valor predeterminado es `false`. En un sistema de archivos de Windows, `use_mmap` no debe establecerse en `true` a menos que el archivo solo se lea una vez y tampoco se escriba. Existen algunos casos límite donde un sistema operativo es similar a Unix pero el sistema de archivos es similar a Windows.

Si `quotes` es `true`, se permite que las columnas encerradas entre comillas dobles (") contengan nuevas líneas y delimitadores de columna. Los caracteres de comillas dobles dentro de un campo entre comillas deben escaparse con otra comilla doble. Especificar `dims` como una tupla de las filas y columnas esperadas (incluyendo el encabezado, si lo hay) puede acelerar la lectura de archivos grandes. Si `comments` es `true`, las líneas que comienzan con `comment_char` y el texto que sigue a `comment_char` en cualquier línea son ignoradas.

# Ejemplos

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
