```
module
```

`module` deklariert ein [`Module`](@ref), das einen separaten globalen Variablen-Arbeitsbereich darstellt. Innerhalb eines Moduls können Sie steuern, welche Namen aus anderen Modulen sichtbar sind (durch Importieren), und festlegen, welche Ihrer Namen öffentlich sein sollen (durch `export` und `public`). Module ermöglichen es Ihnen, Definitionen auf oberster Ebene zu erstellen, ohne sich um Namenskonflikte sorgen zu müssen, wenn Ihr Code zusammen mit dem eines anderen verwendet wird. Siehe den [Handbuchabschnitt über Module](@ref modules) für weitere Details.

# Beispiele

```julia
module Foo
import Base.show
export MyType, foo

struct MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
