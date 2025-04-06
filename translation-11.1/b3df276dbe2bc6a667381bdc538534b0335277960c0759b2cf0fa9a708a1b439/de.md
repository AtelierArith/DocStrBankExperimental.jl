```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

Gibt zurück, ob ein gegebener PkgId im aktiven Projekt vorkompiliert ist.

Standardmäßig folgt diese Überprüfung dem gleichen Ansatz, den das Laden von Code in Bezug darauf verfolgt, wann verschiedene Versionen von Abhängigkeiten derzeit geladen sind, im Vergleich zu dem, was erwartet wird. Um geladene Module zu ignorieren und zu antworten, als ob es sich um eine frische Julia-Sitzung handelt, geben Sie `ignore_loaded=true` an.

!!! compat "Julia 1.10"
    Diese Funktion erfordert mindestens Julia 1.10.

