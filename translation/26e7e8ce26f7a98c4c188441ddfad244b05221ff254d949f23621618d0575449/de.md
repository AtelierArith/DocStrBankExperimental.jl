```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

Konfigurieren Sie das Verhalten für ein Mehrfachauswahlmenü über Schlüsselwortargumente:

  * `checked` ist der String, der angezeigt wird, wenn eine Option ausgewählt wurde. Die Standardwerte sind "[X]" oder "✓", abhängig von `charset`.
  * `unchecked` ist der String, der angezeigt wird, wenn eine Option nicht ausgewählt wurde. Die Standardwerte sind "[ ]" oder "⬚", abhängig von `charset`.

Alle anderen Schlüsselwortargumente sind wie beschrieben für [`TerminalMenus.Config`](@ref). `checked` und `unchecked` werden nicht automatisch ausgegeben und sollten von Ihrer `writeline`-Methode ausgegeben werden.

!!! compat "Julia 1.6"
    `MultiSelectConfig` ist seit Julia 1.6 verfügbar. In älteren Versionen verwenden Sie das globale `CONFIG`.

