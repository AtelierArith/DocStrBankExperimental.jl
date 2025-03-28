```
code_typed(f, types; kw...)
```

Gibt ein Array der typ-inferierten, gesenkten Form (IR) für die Methoden zurück, die der gegebenen generischen Funktion und dem Typsignatur entsprechen.

# Schlüsselwortargumente

  * `optimize::Bool = true`: optional, steuert, ob zusätzliche Optimierungen, wie Inlining, ebenfalls angewendet werden.
  * `debuginfo::Symbol = :default`: optional, steuert die Menge an Code-Metadaten, die im Output vorhanden sind, mögliche Optionen sind `:source` oder `:none`.

# Interne Schlüsselwortargumente

Dieser Abschnitt sollte als intern betrachtet werden und ist nur für diejenigen, die die internen Abläufe des Julia-Compilers verstehen.

  * `world::UInt = Base.get_world_counter()`: optional, steuert das Weltalter, das bei der Suche nach Methoden verwendet wird, verwende das aktuelle Weltalter, wenn nicht angegeben.
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`: optional, steuert den zu verwendenden abstrakten Interpreter, verwende den nativen Interpreter, wenn nicht angegeben.

# Beispiele

Man kann die Argumenttypen in einem Tupel angeben, um das entsprechende `code_typed` zu erhalten.

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
