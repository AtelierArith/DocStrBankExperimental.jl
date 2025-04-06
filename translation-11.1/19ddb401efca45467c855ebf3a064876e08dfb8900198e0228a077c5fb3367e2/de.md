```
sizehint!(s, n; first::Bool=false, shrink::Bool=true) -> s
```

Schlagen Sie vor, dass die Sammlung `s` Kapazität für mindestens `n` Elemente reserviert. Das heißt, wenn Sie erwarten, dass Sie viele Werte in `s` einfügen müssen, können Sie die Kosten für inkrementelle Neuzuweisungen vermeiden, indem Sie dies einmal im Voraus tun; dies kann die Leistung verbessern.

Wenn `first` auf `true` gesetzt ist, wird zusätzlicher Platz vor dem Beginn der Sammlung reserviert. Auf diese Weise können nachfolgende Aufrufe von `pushfirst!` (anstatt von `push!`) schneller werden. Das Bereitstellen dieses Schlüssels kann zu einem Fehler führen, wenn die Sammlung nicht geordnet ist oder wenn `pushfirst!` für diese Sammlung nicht unterstützt wird.

Wenn `shrink=true` (der Standard), kann die Kapazität der Sammlung reduziert werden, wenn ihre aktuelle Kapazität größer als `n` ist.

Siehe auch [`resize!`](@ref).

# Hinweise zum Leistungsmodell

Für Typen, die `sizehint!` unterstützen,

1. `push!` und `append!` Methoden können im Allgemeinen (aber sind nicht verpflichtet) zusätzlichen Speicher vorab zu reservieren. Für Typen, die in `Base` implementiert sind, tun sie dies typischerweise, indem sie eine Heuristik verwenden, die für einen allgemeinen Anwendungsfall optimiert ist.
2. `sizehint!` kann diese Vorabreservierung steuern. Auch hier tut es dies typischerweise für Typen in `Base`.
3. `empty!` ist nahezu kostenfrei (und O(1)) für Typen, die diese Art der Vorabreservierung unterstützen.

!!! compat "Julia 1.11"
    Die Argumente `shrink` und `first` wurden in Julia 1.11 hinzugefügt.

