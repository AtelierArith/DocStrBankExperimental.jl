# [Workflow Tips](@id man-workflow-tips)

Aquí hay algunos consejos para trabajar con Julia de manera eficiente.

## REPL-based workflow

Como ya se elaboró en [The Julia REPL](@ref), el REPL de Julia proporciona una funcionalidad rica que facilita un flujo de trabajo interactivo eficiente. Aquí hay algunos consejos que podrían mejorar aún más tu experiencia en la línea de comandos.

### A basic editor/REPL workflow

Los flujos de trabajo más básicos de Julia implican el uso de un editor de texto junto con la línea de comandos `julia`.

Crea un archivo, digamos `Tmp.jl`, e incluye dentro de él

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

Luego, en el mismo directorio, inicia el REPL de Julia (usando el comando `julia`). Ejecuta el nuevo archivo de la siguiente manera:

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

Explora ideas en el REPL. Guarda buenas ideas en `Tmp.jl`. Para recargar el archivo después de que ha sido modificado, simplemente `inclúyelo` de nuevo.

La clave en lo anterior es que tu código está encapsulado en un módulo. Eso te permite editar las definiciones de `struct` y eliminar métodos, sin reiniciar Julia.

(Explicación: los `struct`s no se pueden editar después de la definición, ni se pueden eliminar métodos. Pero *puedes* sobrescribir la definición de un módulo, que es lo que hacemos cuando volvemos a `include("Tmp.jl")`).

Además, la encapsulación del código en un módulo lo protege de ser influenciado por el estado anterior en el REPL, protegiéndote de errores difíciles de detectar.

## Browser-based workflow

Hay algunas formas de interactuar con Julia en un navegador:

  * Using Pluto notebooks through [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * Usando cuadernos Jupyter a través de [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

Ya sea que estés en el REPL o en IJulia, puedes mejorar tu experiencia de desarrollo con [Revise](https://github.com/timholy/Revise.jl). Es común configurar Revise para que se inicie cada vez que se inicia julia, según las instrucciones en [Revise documentation](https://timholy.github.io/Revise.jl/stable/). Una vez configurado, Revise rastreará los cambios en los archivos de cualquier módulo cargado, y en cualquier archivo cargado en el REPL con `includet` (pero no con `include`); luego puedes editar los archivos y los cambios tendrán efecto sin reiniciar tu sesión de julia. Un flujo de trabajo estándar es similar al flujo de trabajo basado en REPL mencionado anteriormente, con las siguientes modificaciones:

1. Coloca tu código en un módulo en algún lugar de tu ruta de carga. Hay varias opciones para lograr esto, de las cuales dos opciones recomendadas son:

      * Para proyectos a largo plazo, utiliza [PkgTemplates](https://github.com/invenia/PkgTemplates.jl):

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        Esto creará un paquete en blanco, `"MyPkg"`, en tu directorio `.julia/dev`. Ten en cuenta que PkgTemplates te permite controlar muchas opciones diferentes a través de su constructor `Template`.

        En el paso 2 a continuación, edita `MyPkg/src/MyPkg.jl` para cambiar el código fuente y `MyPkg/test/runtests.jl` para las pruebas.
      * Para proyectos "desechables", puedes evitar cualquier necesidad de limpieza haciendo tu trabajo en tu directorio temporal (por ejemplo, `/tmp`).

        Navega a tu directorio temporal y lanza Julia, luego haz lo siguiente:

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        Si reinicias tu sesión de Julia, tendrás que volver a emitir ese comando modificando `LOAD_PATH`.

        En el paso 2 a continuación, edita `MyPkg/src/MyPkg.jl` para cambiar el código fuente y crea cualquier archivo de prueba de tu elección.
2. Desarrolla tu paquete

    *Antes* de cargar cualquier código, asegúrate de estar ejecutando Revise: di `using Revise` o sigue su documentación sobre cómo configurarlo para que se ejecute automáticamente.

    Luego navega al directorio que contiene tu archivo de prueba (aquí asumido como `"runtests.jl"`) y haz lo siguiente:

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    Puedes modificar iterativamente el código en MyPkg en tu editor y volver a ejecutar las pruebas con `include("runtests.jl")`. Generalmente, no deberías necesitar reiniciar tu sesión de Julia para ver que los cambios surtan efecto (sujeto a algunas [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)).
