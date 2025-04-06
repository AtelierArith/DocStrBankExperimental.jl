```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

Configura el comportamiento de los menús de selección a través de argumentos de palabra clave:

  * `scroll_wrap`, si es `true`, hace que el menú se envuelva al desplazarse por encima de la primera o por debajo de la última entrada
  * `ctrl_c_interrupt`, si es `true`, lanza una `InterruptException` si el usuario presiona Ctrl-C durante la selección del menú. Si es `false`, [`TerminalMenus.request`](@ref) devolverá el resultado predeterminado de [`TerminalMenus.selected`](@ref).
  * `charset` afecta los valores predeterminados para `cursor`, `up_arrow` y `down_arrow`, y puede ser `:ascii` o `:unicode`
  * `cursor` es el carácter impreso para indicar la opción que se elegirá al presionar "Enter". Los valores predeterminados son '>' o '→', dependiendo de `charset`.
  * `up_arrow` es el carácter impreso cuando la pantalla no incluye la primera entrada. Los valores predeterminados son '^' o '↑', dependiendo de `charset`.
  * `down_arrow` es el carácter impreso cuando la pantalla no incluye la última entrada. Los valores predeterminados son 'v' o '↓', dependiendo de `charset`.

Los subtipos de `ConfiguredMenu` imprimirán `cursor`, `up_arrow` y `down_arrow` automáticamente según sea necesario, tu método `writeline` no debe imprimirlos.

!!! compat "Julia 1.6"
    `Config` está disponible a partir de Julia 1.6. En versiones anteriores, usa el `CONFIG` global.

