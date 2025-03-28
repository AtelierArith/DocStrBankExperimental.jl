```
StackFrame
```

Stapelinformationen, die den Ausführungskontext darstellen, mit den folgenden Feldern:

  * `func::Symbol`

    Der Name der Funktion, die den Ausführungskontext enthält.
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    Die MethodInstance oder CodeInfo, die den Ausführungskontext enthält (falls sie gefunden werden konnte), oder Modul (für Makroerweiterungen).
  * `file::Symbol`

    Der Pfad zur Datei, die den Ausführungskontext enthält.
  * `line::Int`

    Die Zeilennummer in der Datei, die den Ausführungskontext enthält.
  * `from_c::Bool`

    Wahr, wenn der Code von C stammt.
  * `inlined::Bool`

    Wahr, wenn der Code von einem inlined Frame stammt.
  * `pointer::UInt64`

    Darstellung des Zeigers auf den Ausführungskontext, wie von `backtrace` zurückgegeben.
