```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

Schreibt die Option am Index `idx` in `buf`. `iscursor`, wenn `true`, zeigt an, dass dieses Element sich an der aktuellen Cursorposition befindet (demjenigen, der durch Drücken von "Enter" ausgewählt wird).

Wenn `m` ein `ConfiguredMenu` ist, wird `TerminalMenus` den Cursorindikator drucken. Andernfalls wird vom Aufrufer erwartet, dass er das Drucken entsprechend behandelt.

!!! compat "Julia 1.6"
    `writeline` erfordert Julia 1.6 oder höher.

    In älteren Versionen von Julia war dies `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)` und `m` wird als nicht konfiguriert angenommen. Die Auswahl- und Cursorindikatoren können von `TerminalMenus.CONFIG` abgerufen werden.

    Diese ältere Funktion wird in allen Julia 1.x-Versionen unterstützt, wird jedoch in Julia 2.0 entfernt.

