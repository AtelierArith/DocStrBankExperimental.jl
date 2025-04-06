```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

Gibt ein Vektor von `(Method,Method)`-Paaren von mehrdeutigen Methoden zurück, die in den angegebenen Modulen definiert sind. Verwenden Sie `recursive=true`, um in allen Untermodulen zu testen.

`ambiguous_bottom` steuert, ob Mehrdeutigkeiten, die nur durch `Union{}`-Typparameter ausgelöst werden, einbezogen werden; in den meisten Fällen möchten Sie dies wahrscheinlich auf `false` setzen. Siehe [`Base.isambiguous`](@ref).

Siehe [`Test.detect_unbound_args`](@ref) für eine Erklärung von `allowed_undefineds`.

!!! compat "Julia 1.8"
    `allowed_undefineds` erfordert mindestens Julia 1.8.

