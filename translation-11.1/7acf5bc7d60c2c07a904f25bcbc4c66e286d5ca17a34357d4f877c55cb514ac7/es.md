```
config( <ver argumentos> )
```

Función solo de palabras clave para configurar parámetros del menú global

# Argumentos

  * `charset::Symbol=:na`: caracteres de ui a usar (`:ascii` o `:unicode`); sobrescrito por otros argumentos
  * `cursor::Char='>'|'→'`: carácter a usar para el cursor
  * `up_arrow::Char='^'|'↑'`: carácter a usar para la flecha hacia arriba
  * `down_arrow::Char='v'|'↓'`: carácter a usar para la flecha hacia abajo
  * `checked::String="[X]"|"✓"`: cadena a usar para marcado
  * `unchecked::String="[ ]"|"⬚")`: cadena a usar para desmarcado
  * `scroll::Symbol=:nowrap`: Si `:wrap` envuelve el cursor en la parte superior e inferior, si `:nowrap` no envuelve el cursor
  * `supress_output::Bool=false`: Argumento legado ignorado, pasa `suppress_output` como un argumento de palabra clave a `request` en su lugar.
  * `ctrl_c_interrupt::Bool=true`: Si `false`, devuelve vacío en ^C, si `true` lanza InterruptException() en ^C

!!! compat "Julia 1.6"
    A partir de Julia 1.6, `config` está en desuso. Usa `Config` o `MultiSelectConfig` en su lugar.

