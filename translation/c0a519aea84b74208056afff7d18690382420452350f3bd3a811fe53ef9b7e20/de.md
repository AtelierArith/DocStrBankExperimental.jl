```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

Konfigurieren Sie das Verhalten für Auswahlmenüs über Schlüsselwortargumente:

  * `scroll_wrap`, wenn `true`, bewirkt, dass das Menü beim Scrollen über den ersten oder unter den letzten Eintrag umschlägt
  * `ctrl_c_interrupt`, wenn `true`, wirft eine `InterruptException`, wenn der Benutzer während der Menüauswahl Ctrl-C drückt. Wenn `false`, wird [`TerminalMenus.request`](@ref) das Standardergebnis von [`TerminalMenus.selected`](@ref) zurückgeben.
  * `charset` beeinflusst die Standardwerte für `cursor`, `up_arrow` und `down_arrow` und kann `:ascii` oder `:unicode` sein
  * `cursor` ist das Zeichen, das gedruckt wird, um die Option anzuzeigen, die durch Drücken von "Enter" gewählt wird. Die Standardwerte sind '>' oder '→', abhängig von `charset`.
  * `up_arrow` ist das Zeichen, das gedruckt wird, wenn die Anzeige den ersten Eintrag nicht enthält. Die Standardwerte sind '^' oder '↑', abhängig von `charset`.
  * `down_arrow` ist das Zeichen, das gedruckt wird, wenn die Anzeige den letzten Eintrag nicht enthält. Die Standardwerte sind 'v' oder '↓', abhängig von `charset`.

Untertypen von `ConfiguredMenu` drucken `cursor`, `up_arrow` und `down_arrow` automatisch nach Bedarf, Ihre `writeline`-Methode sollte sie nicht drucken.

!!! compat "Julia 1.6"
    `Config` ist seit Julia 1.6 verfügbar. In älteren Versionen verwenden Sie das globale `CONFIG`.

