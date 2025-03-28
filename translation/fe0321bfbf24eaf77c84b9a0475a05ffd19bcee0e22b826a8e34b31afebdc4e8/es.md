```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

Por favor, lee el [release notes](NEWS.md) para ver qué ha cambiado desde la última versión.

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

A continuación se muestra una lista no exhaustiva de enlaces que serán útiles a medida que aprendas y uses el lenguaje de programación Julia.

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

La computación científica ha requerido tradicionalmente el más alto rendimiento, sin embargo, los expertos en el dominio se han trasladado en gran medida a lenguajes dinámicos más lentos para su trabajo diario. Creemos que hay muchas buenas razones para preferir lenguajes dinámicos para estas aplicaciones, y no esperamos que su uso disminuya. Afortunadamente, el diseño moderno de lenguajes y las técnicas de compilación hacen posible eliminar en gran medida la compensación de rendimiento y proporcionar un único entorno lo suficientemente productivo para la creación de prototipos y lo suficientemente eficiente para implementar aplicaciones intensivas en rendimiento. El lenguaje de programación Julia cumple con este papel: es un lenguaje dinámico flexible, apropiado para la computación científica y numérica, con un rendimiento comparable al de los lenguajes estáticamente tipados tradicionales.

Debido a que el compilador de Julia es diferente de los intérpretes utilizados para lenguajes como Python o R, es posible que al principio encuentres que el rendimiento de Julia es poco intuitivo. Si encuentras que algo es lento, te recomendamos encarecidamente que leas la sección [Performance Tips](@ref man-performance-tips) antes de intentar cualquier otra cosa. Una vez que entiendas cómo funciona Julia, es fácil escribir código que sea casi tan rápido como C.

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia cuenta con tipado opcional, despacho múltiple y un buen rendimiento, logrado mediante inferencia de tipos y [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (y [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)), implementado usando [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine). Es un lenguaje multiparadigma, que combina características de programación imperativa, funcional y orientada a objetos. Julia proporciona facilidad y expresividad para la computación numérica de alto nivel, de la misma manera que lenguajes como R, MATLAB y Python, pero también soporta programación general. Para lograr esto, Julia se basa en la herencia de lenguajes de programación matemática, pero también toma mucho de lenguajes dinámicos populares, incluyendo [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)), y [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)).

Las desviaciones más significativas de Julia con respecto a los lenguajes dinámicos típicos son:

  * El lenguaje base impone muy poco; Julia Base y la biblioteca estándar están escritas en Julia misma, incluyendo operaciones primitivas como la aritmética entera.
  * Un lenguaje rico de tipos para construir y describir objetos, que también se puede utilizar opcionalmente para hacer declaraciones de tipos.
  * La capacidad de definir el comportamiento de la función a través de muchas combinaciones de tipos de argumentos mediante [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)
  * Generación automática de código eficiente y especializado para diferentes tipos de argumentos
  * Buen rendimiento, acercándose al de lenguajes compilados estáticamente como C.

Aunque a veces se habla de lenguajes dinámicos como si fueran "sin tipo", definitivamente no lo son. Cada objeto, ya sea primitivo o definido por el usuario, tiene un tipo. Sin embargo, la falta de declaraciones de tipo en la mayoría de los lenguajes dinámicos significa que no se puede instruir al compilador sobre los tipos de valores, y a menudo no se puede hablar explícitamente sobre tipos en absoluto. En los lenguajes estáticos, por otro lado, aunque se puede – y generalmente se debe – anotar tipos para el compilador, los tipos existen solo en tiempo de compilación y no se pueden manipular o expresar en tiempo de ejecución. En Julia, los tipos son en sí mismos objetos en tiempo de ejecución, y también se pueden usar para transmitir información al compilador.

### [What Makes Julia, Julia?](@id man-what-makes-julia)

Mientras que el programador casual no necesita usar explícitamente tipos o despacho múltiple, estos son las características unificadoras centrales de Julia: las funciones se definen en diferentes combinaciones de tipos de argumentos y se aplican despachando a la definición más específica que coincida. Este modelo es adecuado para la programación matemática, donde es antinatural que el primer argumento "posea" una operación como en el despacho orientado a objetos tradicional. Los operadores son solo funciones con notación especial; para extender la adición a nuevos tipos de datos definidos por el usuario, defines nuevos métodos para la función `+`. El código existente se aplica sin problemas a los nuevos tipos de datos.

En parte debido a la inferencia de tipos en tiempo de ejecución (aumentada por anotaciones de tipo opcionales), y en parte por un fuerte enfoque en el rendimiento desde el inicio del proyecto, la eficiencia computacional de Julia supera a la de otros lenguajes dinámicos e incluso rivaliza con la de lenguajes compilados estáticamente. Para problemas numéricos a gran escala, la velocidad siempre ha sido, sigue siendo y probablemente siempre será crucial: la cantidad de datos que se procesan ha mantenido fácilmente el ritmo con la Ley de Moore en las últimas décadas.

### [Advantages of Julia](@id man-advantages-of-julia)

Julia tiene como objetivo crear una combinación sin precedentes de facilidad de uso, potencia y eficiencia en un solo lenguaje. Además de lo anterior, algunas ventajas de Julia sobre sistemas comparables incluyen:

  * Libre y de código abierto ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * Los tipos definidos por el usuario son tan rápidos y compactos como los incorporados.
  * No es necesario vectorizar el código para mejorar el rendimiento; el código devectorizado es rápido.
  * Diseñado para el paralelismo y la computación distribuida
  * Hilos "verdes" ligeros ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * Sistema de tipos discreto pero poderoso
  * Conversiones y promociones elegantes y extensibles para tipos numéricos y otros tipos
  * Soporte eficiente para [Unicode](https://en.wikipedia.org/wiki/Unicode), incluyendo pero no limitado a [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * Llama a funciones C directamente (sin envolturas ni APIs especiales necesarias)
  * Capacidades potentes similares a un shell para gestionar otros procesos
  * Macros y otras facilidades de metaprogramación al estilo Lisp
