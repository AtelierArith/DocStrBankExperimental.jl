```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

Rufen Sie eine Funktion in einer C-exportierten Shared Library auf, die durch `library.function_name` angegeben ist, wobei `library` eine String-Konstante oder ein Literal ist. Die Bibliothek kann weggelassen werden, in diesem Fall wird der `function_name` im aktuellen Prozess aufgelöst. Alternativ kann `@ccall` auch verwendet werden, um einen Funktionszeiger `$function_pointer` aufzurufen, wie er beispielsweise von `dlsym` zurückgegeben wird.

Jeder `argvalue` zu `@ccall` wird in den entsprechenden `argtype` umgewandelt, indem automatisch Aufrufe von `unsafe_convert(argtype, cconvert(argtype, argvalue))` eingefügt werden. (Siehe auch die Dokumentation für [`unsafe_convert`](@ref Base.unsafe_convert) und [`cconvert`](@ref Base.cconvert) für weitere Details.) In den meisten Fällen führt dies einfach zu einem Aufruf von `convert(argtype, argvalue)`.

# Beispiele

```
@ccall strlen(s::Cstring)::Csize_t
```

Dies ruft die C-Standardbibliotheksfunktion auf:

```
size_t strlen(char *)
```

mit einer Julia-Variablen namens `s`. Siehe auch `ccall`.

Varargs werden mit der folgenden Konvention unterstützt:

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

Das Semikolon wird verwendet, um erforderliche Argumente (von denen mindestens eines vorhanden sein muss) von variadischen Argumenten zu trennen.

Beispiel mit einer externen Bibliothek:

```
# C-Signatur von g_uri_escape_string:
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

Das String-Literal könnte auch direkt vor dem Funktionsnamen verwendet werden, wenn gewünscht `"libglib-2.0".g_uri_escape_string(...`
