```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

Appeler une fonction dans une bibliothèque partagée exportée par C, spécifiée par `library.function_name`, où `library` est une constante ou un littéral de chaîne. La bibliothèque peut être omise, auquel cas le `function_name` est résolu dans le processus actuel. Alternativement, `@ccall` peut également être utilisé pour appeler un pointeur de fonction `$function_pointer`, tel que celui retourné par `dlsym`.

Chaque `argvalue` à `@ccall` est converti en `argtype` correspondant, par insertion automatique d'appels à `unsafe_convert(argtype, cconvert(argtype, argvalue))`. (Voir aussi la documentation pour [`unsafe_convert`](@ref Base.unsafe_convert) et [`cconvert`](@ref Base.cconvert) pour plus de détails.) Dans la plupart des cas, cela se traduit simplement par un appel à `convert(argtype, argvalue)`.

# Exemples

```
@ccall strlen(s::Cstring)::Csize_t
```

Cela appelle la fonction de la bibliothèque standard C :

```
size_t strlen(char *)
```

avec une variable Julia nommée `s`. Voir aussi `ccall`.

Les varargs sont pris en charge avec la convention suivante :

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

Le point-virgule est utilisé pour séparer les arguments requis (dont il doit y avoir au moins un) des arguments variadiques.

Exemple utilisant une bibliothèque externe :

```
# Signature C de g_uri_escape_string:
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

Le littéral de chaîne pourrait également être utilisé directement avant le nom de la fonction, si désiré `"libglib-2.0".g_uri_escape_string(...`
