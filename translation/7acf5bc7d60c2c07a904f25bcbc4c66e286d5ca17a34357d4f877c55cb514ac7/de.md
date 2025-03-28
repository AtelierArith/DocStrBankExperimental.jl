```
config( <siehe Argumente> )
```

Keyword-only Funktion zur Konfiguration globaler Menüparameter

# Argumente

  * `charset::Symbol=:na`: UI-Zeichen, die verwendet werden sollen (`:ascii` oder `:unicode`); von anderen Argumenten überschrieben
  * `cursor::Char='>'|'→'`: Zeichen, das für den Cursor verwendet werden soll
  * `up_arrow::Char='^'|'↑'`: Zeichen, das für den Aufwärtspfeil verwendet werden soll
  * `down_arrow::Char='v'|'↓'`: Zeichen, das für den Abwärtspfeil verwendet werden soll
  * `checked::String="[X]"|"✓"`: Zeichenfolge, die für überprüft verwendet werden soll
  * `unchecked::String="[ ]"|"⬚")`: Zeichenfolge, die für nicht überprüft verwendet werden soll
  * `scroll::Symbol=:nowrap`: Wenn `:wrap`, den Cursor oben und unten umwickeln, wenn `:nowrap`, den Cursor nicht umwickeln
  * `supress_output::Bool=false`: Ignoriertes veraltetes Argument, übergeben Sie `suppress_output` stattdessen als Schlüsselwortargument an `request`.
  * `ctrl_c_interrupt::Bool=true`: Wenn `false`, leer zurückgeben bei ^C, wenn `true`, InterruptException() bei ^C auslösen

!!! compat "Julia 1.6"
    Ab Julia 1.6 ist `config` veraltet. Verwenden Sie stattdessen `Config` oder `MultiSelectConfig`.

