```
módulo
```

`módulo` declara un [`Módulo`](@ref), que es un espacio de trabajo de variables globales separado. Dentro de un módulo, puedes controlar qué nombres de otros módulos son visibles (a través de la importación) y especificar cuáles de tus nombres están destinados a ser públicos (a través de `export` y `public`). Los módulos te permiten crear definiciones de nivel superior sin preocuparte por conflictos de nombres cuando tu código se utiliza junto con el de otra persona. Consulta la [sección del manual sobre módulos](@ref modules) para más detalles.

# Ejemplos

```julia
módulo Foo
importar Base.show
exportar MyType, foo

estructura MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
