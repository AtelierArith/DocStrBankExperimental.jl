# Documentación

Las funciones, métodos y tipos pueden ser documentados colocando una cadena antes de la definición:

```
"""
# La Función Foo
`foo(x)`: Foo la vida de `x`.
"""
foo(x) = ...
```

El macro `@doc` se puede usar directamente para establecer y recuperar documentación / metadatos. El macro tiene un análisis especial para que el objeto documentado pueda aparecer en la siguiente línea:

```
@doc "blah"
function foo() ...
```

Por defecto, la documentación se escribe en Markdown, pero cualquier objeto puede ser utilizado como el primer argumento.

## Documentando objetos por separado de sus definiciones

Puedes documentar un objeto antes o después de su definición con

```
@doc "foo" function_to_doc
@doc "bar" TypeToDoc
```

Para macros, la sintaxis es `@doc "macro doc" :(Module.@macro)` o `@doc "macro doc" :(string_macro"")` para macros de cadena. Sin la comilla `:()` la expansión de la macro será documentada.

## Recuperando Documentación

Puedes recuperar docs para funciones, macros y otros objetos de la siguiente manera:

```
@doc foo
@doc @time
@doc md""
```

## Funciones y Métodos

Colocar documentación antes de una definición de método (por ejemplo, `function foo() ...` o `foo() = ...`) hará que ese método específico sea documentado, en lugar de toda la función. Los docs de los métodos se concatenan en el orden en que fueron definidos para proporcionar docs para la función.
