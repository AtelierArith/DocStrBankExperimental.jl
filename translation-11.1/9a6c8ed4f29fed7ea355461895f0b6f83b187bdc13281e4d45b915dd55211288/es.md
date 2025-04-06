```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

Llama a una función en una biblioteca compartida exportada en C, especificada por `library.function_name`, donde `library` es una constante o literal de cadena. La biblioteca puede omitirse, en cuyo caso `function_name` se resuelve en el proceso actual. Alternativamente, `@ccall` también se puede usar para llamar a un puntero de función `$function_pointer`, como uno devuelto por `dlsym`.

Cada `argvalue` a `@ccall` se convierte al correspondiente `argtype`, mediante la inserción automática de llamadas a `unsafe_convert(argtype, cconvert(argtype, argvalue))`. (Véase también la documentación de [`unsafe_convert`](@ref Base.unsafe_convert) y [`cconvert`](@ref Base.cconvert) para más detalles.) En la mayoría de los casos, esto simplemente resulta en una llamada a `convert(argtype, argvalue)`.

# Ejemplos

```
@ccall strlen(s::Cstring)::Csize_t
```

Esto llama a la función de la biblioteca estándar de C:

```
size_t strlen(char *)
```

con una variable de Julia llamada `s`. Véase también `ccall`.

Se admiten varargs con la siguiente convención:

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

El punto y coma se utiliza para separar los argumentos requeridos (de los cuales debe haber al menos uno) de los argumentos variádicos.

Ejemplo usando una biblioteca externa:

```
# Firma C de g_uri_escape_string:
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

El literal de cadena también podría usarse directamente antes del nombre de la función, si se desea `"libglib-2.0".g_uri_escape_string(...`
