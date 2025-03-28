# [Code Loading](@id code-loading)

!!! note
    Este capítulo cubre los detalles técnicos de la carga de paquetes. Para instalar paquetes, utiliza [`Pkg`](@ref Pkg), el administrador de paquetes integrado de Julia, para agregar paquetes a tu entorno activo. Para usar paquetes que ya están en tu entorno activo, escribe `import X` o `using X`, como se describe en [Modules documentation](@ref modules).


## Definitions

Julia tiene dos mecanismos para cargar código:

1. **Inclusión de código:** p. ej. `include("source.jl")`. La inclusión te permite dividir un solo programa en múltiples archivos de origen. La expresión `include("source.jl")` hace que el contenido del archivo `source.jl` se evalúe en el ámbito global del módulo donde ocurre la llamada a `include`. Si se llama a `include("source.jl")` múltiples veces, `source.jl` se evalúa múltiples veces. La ruta incluida, `source.jl`, se interpreta en relación con el archivo donde ocurre la llamada a `include`. Esto facilita la reubicación de un subárbol de archivos de origen. En el REPL, las rutas incluidas se interpretan en relación con el directorio de trabajo actual, [`pwd()`](@ref).
2. **Carga de paquetes:** p. ej. `import X` o `using X`. El mecanismo de importación te permite cargar un paquete—es decir, una colección independiente y reutilizable de código Julia, envuelta en un módulo—y hace que el módulo resultante esté disponible bajo el nombre `X` dentro del módulo que lo importa. Si el mismo paquete `X` se importa múltiples veces en la misma sesión de Julia, solo se carga la primera vez; en importaciones posteriores, el módulo importador obtiene una referencia al mismo módulo. Sin embargo, ten en cuenta que `import X` puede cargar diferentes paquetes en diferentes contextos: `X` puede referirse a un paquete llamado `X` en el proyecto principal, pero potencialmente a diferentes paquetes también llamados `X` en cada dependencia. Más sobre esto a continuación.

La inclusión de código es bastante directa y simple: evalúa el archivo fuente dado en el contexto del llamador. La carga de paquetes se basa en la inclusión de código y sirve a un [different purpose](@ref modules). El resto de este capítulo se centra en el comportamiento y la mecánica de la carga de paquetes.

Un *paquete* es un árbol de código fuente con un diseño estándar que proporciona funcionalidad que puede ser reutilizada por otros proyectos de Julia. Un paquete se carga mediante las declaraciones `import X` o `using X`. Estas declaraciones también hacen que el módulo llamado `X`, que resulta de cargar el código del paquete, esté disponible dentro del módulo donde ocurre la declaración de importación. El significado de `X` en `import X` depende del contexto: qué paquete `X` se carga depende del código en el que ocurre la declaración. Así, el manejo de `import X` ocurre en dos etapas: primero, determina **qué** paquete se define como `X` en este contexto; segundo, determina **dónde** se encuentra ese paquete `X` en particular.

Estas preguntas se responden buscando a través de los entornos de proyecto listados en [`LOAD_PATH`](@ref) para archivos de proyecto (`Project.toml` o `JuliaProject.toml`), archivos de manifiesto (`Manifest.toml` o `JuliaManifest.toml`, o los mismos nombres con el sufijo `-v{mayor}.{menor}.toml` para versiones específicas), o carpetas de archivos fuente.

## Federation of packages

La mayoría de las veces, un paquete es identificable de manera única simplemente por su nombre. Sin embargo, a veces un proyecto puede encontrarse en una situación en la que necesita usar dos paquetes diferentes que comparten el mismo nombre. Si bien es posible que puedas solucionar esto renombrando uno de los paquetes, verse obligado a hacerlo puede ser muy disruptivo en una base de código grande y compartida. En su lugar, el mecanismo de carga de código de Julia permite que el mismo nombre de paquete se refiera a diferentes paquetes en diferentes componentes de una aplicación.

Julia admite la gestión de paquetes federados, lo que significa que múltiples partes independientes pueden mantener tanto paquetes públicos como privados y registros de paquetes, y que los proyectos pueden depender de una mezcla de paquetes públicos y privados de diferentes registros. Los paquetes de varios registros se instalan y gestionan utilizando un conjunto común de herramientas y flujos de trabajo. El gestor de paquetes `Pkg` que se incluye con Julia te permite instalar y gestionar las dependencias de tus proyectos. Ayuda a crear y manipular archivos de proyecto (que describen de qué otros proyectos depende tu proyecto) y archivos de manifiesto (que capturan versiones exactas del gráfico completo de dependencias de tu proyecto).

Una consecuencia de la federación es que no puede haber una autoridad central para la nomenclatura de paquetes. Diferentes entidades pueden usar el mismo nombre para referirse a paquetes no relacionados. Esta posibilidad es inevitable ya que estas entidades no coordinan y pueden no conocerse entre sí. Debido a la falta de una autoridad central de nomenclatura, un solo proyecto puede terminar dependiendo de diferentes paquetes que tienen el mismo nombre. El mecanismo de carga de paquetes de Julia no requiere que los nombres de los paquetes sean globalmente únicos, incluso dentro del gráfico de dependencias de un solo proyecto. En cambio, los paquetes se identifican por [universally unique identifiers](https://en.wikipedia.org/wiki/Universally_unique_identifier) (UUIDs), que se asignan cuando se crea cada paquete. Por lo general, no tendrás que trabajar directamente con estos identificadores de 128 bits algo engorrosos, ya que `Pkg` se encargará de generarlos y rastrearlos por ti. Sin embargo, estos UUIDs proporcionan la respuesta definitiva a la pregunta de *"¿a qué paquete se refiere `X`?"*

Dado que el problema de nombramiento descentralizado es algo abstracto, puede ser útil recorrer un escenario concreto para entender el problema. Supongamos que estás desarrollando una aplicación llamada `App`, que utiliza dos paquetes: `Pub` y `Priv`. `Priv` es un paquete privado que tú creaste, mientras que `Pub` es un paquete público que usas pero no controlas. Cuando creaste `Priv`, no había ningún paquete público con el nombre `Priv`. Sin embargo, posteriormente, se ha publicado un paquete no relacionado también llamado `Priv` que se ha vuelto popular. De hecho, el paquete `Pub` ha comenzado a usarlo. Por lo tanto, cuando actualices `Pub` para obtener las últimas correcciones de errores y características, `App` terminará dependiendo de dos paquetes diferentes llamados `Priv`, sin que tú hayas hecho nada más que actualizar. `App` tiene una dependencia directa de tu paquete privado `Priv`, y una dependencia indirecta, a través de `Pub`, del nuevo paquete público `Priv`. Dado que estos dos paquetes `Priv` son diferentes pero ambos son necesarios para que `App` continúe funcionando correctamente, la expresión `import Priv` debe referirse a diferentes paquetes `Priv` dependiendo de si ocurre en el código de `App` o en el código de `Pub`. Para manejar esto, el mecanismo de carga de paquetes de Julia distingue los dos paquetes `Priv` por su UUID y elige el correcto según su contexto (el módulo que llamó a `import`). Cómo funciona esta distinción se determina por los entornos, como se explica en las secciones siguientes.

## Environments

Un *entorno* determina lo que significan `import X` y `using X` en varios contextos de código y qué archivos causan que se carguen estas declaraciones. Julia entiende dos tipos de entornos:

1. **Un entorno de proyecto** es un directorio con un archivo de proyecto y un archivo de manifiesto opcional, y forma un *entorno explícito*. El archivo de proyecto determina cuáles son los nombres e identidades de las dependencias directas de un proyecto. El archivo de manifiesto, si está presente, proporciona un gráfico de dependencias completo, incluyendo todas las dependencias directas e indirectas, versiones exactas de cada dependencia y suficiente información para localizar y cargar la versión correcta.
2. **Un directorio de paquete** es un directorio que contiene los árboles de origen de un conjunto de paquetes como subdirectorios, y forma un *entorno implícito*. Si `X` es un subdirectorio de un directorio de paquete y `X/src/X.jl` existe, entonces el paquete `X` está disponible en el entorno del directorio de paquete y `X/src/X.jl` es el archivo fuente por el cual se carga.

Estos se pueden mezclar para crear **un entorno apilado**: un conjunto ordenado de entornos de proyecto y directorios de paquetes, superpuestos para formar un único entorno compuesto. Las reglas de precedencia y visibilidad luego se combinan para determinar qué paquetes están disponibles y de dónde se cargan. La ruta de carga de Julia forma un entorno apilado, por ejemplo.

Estos entornos sirven para diferentes propósitos:

  * Los entornos de proyecto proporcionan **reproducibilidad**. Al registrar un entorno de proyecto en el control de versiones—por ejemplo, un repositorio git—junto con el resto del código fuente del proyecto, puedes reproducir el estado exacto del proyecto y todas sus dependencias. El archivo de manifiesto, en particular, captura la versión exacta de cada dependencia, identificada por un hash criptográfico de su árbol fuente, lo que hace posible que `Pkg` recupere las versiones correctas y se asegure de que estás ejecutando el código exacto que se registró para todas las dependencias.
  * Los directorios de paquetes proporcionan **conveniencia** cuando un entorno de proyecto completo y cuidadosamente rastreado no es necesario. Son útiles cuando deseas colocar un conjunto de paquetes en algún lugar y poder usarlos directamente, sin necesidad de crear un entorno de proyecto para ellos.
  * Los entornos apilados permiten **agregar** herramientas al entorno principal. Puedes añadir un entorno de herramientas de desarrollo al final de la pila para que estén disponibles desde el REPL y los scripts, pero no desde dentro de los paquetes.

A un alto nivel, cada entorno define conceptualmente tres mapas: raíces, gráfico y rutas. Al resolver el significado de `import X`, se utilizan los mapas de raíces y gráfico para determinar la identidad de `X`, mientras que el mapa de rutas se utiliza para localizar el código fuente de `X`. Los roles específicos de los tres mapas son:

  * **raíces:** `nombre::Símbolo` ⟶ `uuid::UUID`

    Un mapa de raíces del entorno asigna nombres de paquetes a UUIDs para todas las dependencias de nivel superior que el entorno pone a disposición del proyecto principal (es decir, las que se pueden cargar en `Main`). Cuando Julia encuentra `import X` en el proyecto principal, busca la identidad de `X` como `roots[:X]`.
  * **gráfico:** `context::UUID` ⟶ `name::Symbol` ⟶ `uuid::UUID`

    Un gráfico de entorno es un mapa multinivel que asigna, para cada UUID de `contexto`, un mapa de nombres a UUIDs, similar al mapa de raíces pero específico para ese `contexto`. Cuando Julia ve `import X` en el código del paquete cuyo UUID es `contexto`, busca la identidad de `X` como `graph[contexto][:X]`. En particular, esto significa que `import X` puede referirse a diferentes paquetes dependiendo del `contexto`.
  * **rutas:** `uuid::UUID` × `nombre::Symbol` ⟶ `ruta::String`

    El mapa de rutas asigna a cada par UUID-nombre de paquete, la ubicación del archivo fuente del punto de entrada de ese paquete. Después de que la identidad de `X` en `import X` se ha resuelto a un UUID a través de roots o graph (dependiendo de si se carga desde el proyecto principal o una dependencia), Julia determina qué archivo cargar para adquirir `X` buscando `paths[uuid,:X]` en el entorno. Incluir este archivo debería definir un módulo llamado `X`. Una vez que este paquete está cargado, cualquier importación subsiguiente que se resuelva al mismo `uuid` creará un nuevo enlace al módulo del paquete ya cargado.

Cada tipo de entorno define estos tres mapas de manera diferente, como se detalla en las siguientes secciones.

!!! note
    Para facilitar la comprensión, los ejemplos a lo largo de este capítulo muestran estructuras de datos completas para raíces, gráficos y caminos. Sin embargo, el código de carga de paquetes de Julia no crea explícitamente estos. En su lugar, calcula de manera perezosa solo lo que necesita de cada estructura para cargar un paquete dado.


### Project environments

Un entorno de proyecto se determina por un directorio que contiene un archivo de proyecto llamado `Project.toml`, y opcionalmente un archivo de manifiesto llamado `Manifest.toml`. Estos archivos también pueden llamarse `JuliaProject.toml` y `JuliaManifest.toml`, en cuyo caso se ignoran `Project.toml` y `Manifest.toml`. Esto permite la coexistencia con otras herramientas que podrían considerar significativos los archivos llamados `Project.toml` y `Manifest.toml`. Sin embargo, para proyectos puramente de Julia, se prefieren los nombres `Project.toml` y `Manifest.toml`. Sin embargo, a partir de Julia v1.10.8, `(Julia)Manifest-v{major}.{minor}.toml` se reconoce como un formato para hacer que una versión específica de Julia use un archivo de manifiesto específico, es decir, en la misma carpeta, un `Manifest-v1.11.toml` sería utilizado por v1.11 y `Manifest.toml` por cualquier otra versión de Julia.

Las raíces, el gráfico y los mapas de caminos de un entorno de proyecto se definen de la siguiente manera:

**El mapa de raíces** del entorno se determina por el contenido del archivo del proyecto, específicamente, sus entradas de nivel superior `name` y `uuid` y su sección `[deps]` (todas opcionales). Considera el siguiente archivo de proyecto de ejemplo para la aplicación hipotética, `App`, como se describió anteriormente:

```toml
name = "App"
uuid = "8f986787-14fe-4607-ba5d-fbff2944afa9"

[deps]
Priv = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
Pub  = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
```

Este archivo de proyecto implica el siguiente mapa de raíces, si se representara mediante un diccionario de Julia:

```julia
roots = Dict(
    :App  => UUID("8f986787-14fe-4607-ba5d-fbff2944afa9"),
    :Priv => UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"),
    :Pub  => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
)
```

Dada este mapa de raíces, en el código de `App`, la declaración `import Priv` hará que Julia busque `roots[:Priv]`, lo que da como resultado `ba13f791-ae1d-465a-978b-69c3ad90f72b`, el UUID del paquete `Priv` que se debe cargar en ese contexto. Este UUID identifica qué paquete `Priv` cargar y usar cuando la aplicación principal evalúa `import Priv`.

**El gráfico de dependencias** de un entorno de proyecto se determina por el contenido del archivo de manifiesto, si está presente. Si no hay un archivo de manifiesto, el gráfico está vacío. Un archivo de manifiesto contiene una estrofa para cada una de las dependencias directas o indirectas de un proyecto. Para cada dependencia, el archivo enumera el UUID del paquete y un hash del árbol de origen o una ruta explícita al código fuente. Considera el siguiente ejemplo de archivo de manifiesto para `App`:

```toml
[[Priv]] # the private one
deps = ["Pub", "Zebra"]
uuid = "ba13f791-ae1d-465a-978b-69c3ad90f72b"
path = "deps/Priv"

[[Priv]] # the public one
uuid = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
git-tree-sha1 = "1bf63d3be994fe83456a03b874b409cfd59a6373"
version = "0.1.5"

[[Pub]]
uuid = "c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"
git-tree-sha1 = "9ebd50e2b0dd1e110e842df3b433cb5869b0dd38"
version = "2.1.4"

  [Pub.deps]
  Priv = "2d15fe94-a1f7-436c-a4d8-07a9a496e01c"
  Zebra = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"

[[Zebra]]
uuid = "f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"
git-tree-sha1 = "e808e36a5d7173974b90a15a353b564f3494092f"
version = "3.4.2"
```

Este archivo de manifiesto describe un posible gráfico de dependencias completo para el proyecto `App`:

  * Hay dos paquetes diferentes llamados `Priv` que utiliza la aplicación. Utiliza un paquete privado, que es una dependencia raíz, y uno público, que es una dependencia indirecta a través de `Pub`. Estos se diferencian por sus UUIDs distintos y tienen diferentes dependencias:

      * El privado `Priv` depende de los paquetes `Pub` y `Zebra`.
      * El público `Priv` no tiene dependencias.
  * La aplicación también depende del paquete `Pub`, que a su vez depende del público `Priv` y del mismo paquete `Zebra` del que depende el paquete privado `Priv`.

Este gráfico de dependencias representado como un diccionario, se ve así:

```julia
graph = Dict(
    # Priv – the private one:
    UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b") => Dict(
        :Pub   => UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Priv – the public one:
    UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c") => Dict(),
    # Pub:
    UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1") => Dict(
        :Priv  => UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"),
        :Zebra => UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"),
    ),
    # Zebra:
    UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62") => Dict(),
)
```

Dada esta `grafica` de dependencias, cuando Julia ve `import Priv` en el paquete `Pub`—que tiene el UUID `c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1`—busca:

```julia
graph[UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1")][:Priv]
```

y obtiene `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`, lo que indica que en el contexto del paquete `Pub`, `import Priv` se refiere al paquete público `Priv`, en lugar del privado del cual la aplicación depende directamente. Así es como el nombre `Priv` puede referirse a diferentes paquetes en el proyecto principal que en uno de los paquetes de sus dependencias, lo que permite nombres duplicados en el ecosistema de paquetes.

¿Qué sucede si se evalúa `import Zebra` en la base de código principal de `App`? Dado que `Zebra` no aparece en el archivo del proyecto, la importación fallará a pesar de que `Zebra` *sí* aparece en el archivo de manifiesto. Además, si `import Zebra` ocurre en el paquete público `Priv`—el que tiene el UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—también fallará ya que ese paquete `Priv` no tiene dependencias declaradas en el archivo de manifiesto y, por lo tanto, no puede cargar ningún paquete. El paquete `Zebra` solo puede ser cargado por paquetes para los cuales aparece como una dependencia explícita en el archivo de manifiesto: el paquete `Pub` y uno de los paquetes `Priv`.

**El mapa de rutas** de un entorno de proyecto se extrae del archivo de manifiesto. La ruta de un paquete `uuid` llamado `X` se determina por estas reglas (en orden):

1. Si el archivo del proyecto en el directorio coincide con `uuid` y el nombre `X`, entonces ya sea:

      * Tiene una entrada `path` de nivel superior, luego `uuid` se mapeará a esa ruta, interpretada en relación con el directorio que contiene el archivo del proyecto.
      * De lo contrario, `uuid` se mapea a `src/X.jl` en relación con el directorio que contiene el archivo del proyecto.
2. Si no es el caso anterior y el archivo del proyecto tiene un archivo de manifiesto correspondiente y el manifiesto contiene una estrofa que coincide con `uuid`, entonces:

      * Si tiene una entrada `path`, use esa ruta (relativa al directorio que contiene el archivo de manifiesto).
      * Si tiene una entrada `git-tree-sha1`, calcule una función hash determinista de `uuid` y `git-tree-sha1`, llámela `slug`, y busque un directorio llamado `packages/X/$slug` en cada directorio en el arreglo global `DEPOT_PATH` de Julia. Use el primer directorio que exista.

Si alguno de estos resultados tiene éxito, la ruta al punto de entrada del código fuente será ya sea ese resultado, la ruta relativa desde ese resultado más `src/X.jl`; de lo contrario, no hay mapeo de ruta para `uuid`. Al cargar `X`, si no se encuentra ninguna ruta de código fuente, la búsqueda fallará y se puede solicitar al usuario que instale la versión de paquete apropiada o que tome otras medidas correctivas (por ejemplo, declarar `X` como una dependencia).

En el archivo de manifiesto de ejemplo anterior, para encontrar la ruta del primer paquete `Priv`, el que tiene el UUID `ba13f791-ae1d-465a-978b-69c3ad90f72b`, Julia busca su estrofa en el archivo de manifiesto, ve que tiene una entrada `path`, mira `deps/Priv` en relación con el directorio del proyecto `App`—supongamos que el código de `App` vive en `/home/me/projects/App`—ve que `/home/me/projects/App/deps/Priv` existe y, por lo tanto, carga `Priv` desde allí.

Si, por otro lado, Julia estaba cargando el *otro* paquete `Priv`—el que tiene UUID `2d15fe94-a1f7-436c-a4d8-07a9a496e01c`—encuentra su estrofa en el manifiesto, ve que no tiene una entrada `path`, pero que sí tiene una entrada `git-tree-sha1`. Luego calcula el `slug` para este par UUID/SHA-1, que es `HDkrT` (los detalles exactos de este cálculo no son importantes, pero son consistentes y deterministas). Esto significa que la ruta a este paquete `Priv` será `packages/Priv/HDkrT/src/Priv.jl` en uno de los depósitos de paquetes. Supongamos que el contenido de `DEPOT_PATH` es `["/home/me/.julia", "/usr/local/julia"]`, entonces Julia mirará las siguientes rutas para ver si existen:

1. `/home/me/.julia/packages/Priv/HDkrT`
2. `/usr/local/julia/packages/Priv/HDkrT`

Julia utiliza el primero de estos que existe para intentar cargar el paquete público `Priv` desde el archivo `packages/Priv/HDKrT/src/Priv.jl` en el depósito donde se encontró.

Aquí hay una representación de un posible mapa de rutas para nuestro proyecto de ejemplo `App`, tal como se proporciona en el Manifiesto dado arriba para el gráfico de dependencias, después de buscar en el sistema de archivos local:

```julia
paths = Dict(
    # Priv – the private one:
    (UUID("ba13f791-ae1d-465a-978b-69c3ad90f72b"), :Priv) =>
        # relative entry-point inside `App` repo:
        "/home/me/projects/App/deps/Priv/src/Priv.jl",
    # Priv – the public one:
    (UUID("2d15fe94-a1f7-436c-a4d8-07a9a496e01c"), :Priv) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Priv/HDkr/src/Priv.jl",
    # Pub:
    (UUID("c07ecb7d-0dc9-4db7-8803-fadaaeaf08e1"), :Pub) =>
        # package installed in the user depot:
        "/home/me/.julia/packages/Pub/oKpw/src/Pub.jl",
    # Zebra:
    (UUID("f7a24cb4-21fc-4002-ac70-f0e3a0dd3f62"), :Zebra) =>
        # package installed in the system depot:
        "/usr/local/julia/packages/Zebra/me9k/src/Zebra.jl",
)
```

Este mapa de ejemplo incluye tres tipos diferentes de ubicaciones de paquetes (el primero y el tercero son parte de la ruta de carga predeterminada):

1. El paquete privado `Priv` es "[vendored](https://stackoverflow.com/a/35109534)" dentro del repositorio `App`.
2. Los paquetes públicos `Priv` y `Zebra` están en el depósito del sistema, donde residen los paquetes instalados y gestionados por el administrador del sistema. Estos están disponibles para todos los usuarios del sistema.
3. El paquete `Pub` está en el depósito del usuario, donde viven los paquetes instalados por el usuario. Estos solo están disponibles para el usuario que los instaló.

### Package directories

Los directorios de paquetes proporcionan un tipo de entorno más simple sin la capacidad de manejar colisiones de nombres. En un directorio de paquetes, el conjunto de paquetes de nivel superior es el conjunto de subdirectorios que "se parecen" a paquetes. Un paquete `X` existe en un directorio de paquetes si el directorio contiene uno de los siguientes archivos de "punto de entrada":

  * `X.jl`
  * `X/src/X.jl`
  * `X.jl/src/X.jl`

Qué dependencias puede importar un paquete en un directorio de paquetes depende de si el paquete contiene un archivo de proyecto:

  * Si tiene un archivo de proyecto, solo puede importar aquellos paquetes que están identificados en la sección `[deps]` del archivo del proyecto.
  * Si no tiene un archivo de proyecto, puede importar cualquier paquete de nivel superior, es decir, los mismos paquetes que se pueden cargar en `Main` o en el REPL.

**El mapa de raíces** se determina examinando el contenido del directorio del paquete para generar una lista de todos los paquetes que existen. Además, se asignará un UUID a cada entrada de la siguiente manera: Para un paquete dado encontrado dentro de la carpeta `X`...

1. Si `X/Project.toml` existe y tiene una entrada `uuid`, entonces `uuid` es ese valor.
2. Si `X/Project.toml` existe pero *no* tiene una entrada UUID de nivel superior, `uuid` es un UUID ficticio generado al hash de la ruta canónica (real) a `X/Project.toml`.
3. De lo contrario (si `Project.toml` no existe), entonces `uuid` es el todo-cero [nil UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier#Nil_UUID).

**El gráfico de dependencias** de un directorio de proyecto se determina por la presencia y el contenido de los archivos del proyecto en el subdirectorio de cada paquete. Las reglas son:

  * Si un subdirectorio de paquete no tiene un archivo de proyecto, entonces se omite del gráfico y las declaraciones de importación en su código se tratan como de nivel superior, al igual que el proyecto principal y el REPL.
  * Si un subdirectorio de paquete tiene un archivo de proyecto, entonces la entrada del gráfico para su UUID es el mapa `[deps]` del archivo de proyecto, que se considera vacío si la sección está ausente.

Como ejemplo, supongamos que un directorio de paquete tiene la siguiente estructura y contenido:

```
Aardvark/
    src/Aardvark.jl:
        import Bobcat
        import Cobra

Bobcat/
    Project.toml:
        [deps]
        Cobra = "4725e24d-f727-424b-bca0-c4307a3456fa"
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Bobcat.jl:
        import Cobra
        import Dingo

Cobra/
    Project.toml:
        uuid = "4725e24d-f727-424b-bca0-c4307a3456fa"
        [deps]
        Dingo = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Cobra.jl:
        import Dingo

Dingo/
    Project.toml:
        uuid = "7a7925be-828c-4418-bbeb-bac8dfc843bc"

    src/Dingo.jl:
        # no imports
```

Aquí hay una estructura de raíces correspondiente, representada como un diccionario:

```julia
roots = Dict(
    :Aardvark => UUID("00000000-0000-0000-0000-000000000000"), # no project file, nil UUID
    :Bobcat   => UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), # dummy UUID based on path
    :Cobra    => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), # UUID from project file
    :Dingo    => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), # UUID from project file
)
```

Aquí está la estructura de gráfico correspondiente, representada como un diccionario:

```julia
graph = Dict(
    # Bobcat:
    UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf") => Dict(
        :Cobra => UUID("4725e24d-f727-424b-bca0-c4307a3456fa"),
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Cobra:
    UUID("4725e24d-f727-424b-bca0-c4307a3456fa") => Dict(
        :Dingo => UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"),
    ),
    # Dingo:
    UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc") => Dict(),
)
```

Algunas reglas generales a tener en cuenta:

1. Un paquete sin un archivo de proyecto puede depender de cualquier dependencia de nivel superior, y dado que cada paquete en un directorio de paquetes está disponible a nivel superior, puede importar todos los paquetes en el entorno.
2. Un paquete con un archivo de proyecto no puede depender de uno sin un archivo de proyecto, ya que los paquetes con archivos de proyecto solo pueden cargar paquetes en `graph` y los paquetes sin archivos de proyecto no aparecen en `graph`.
3. Un paquete con un archivo de proyecto pero sin un UUID explícito solo puede ser dependido por paquetes sin archivos de proyecto, ya que los UUIDs ficticios asignados a estos paquetes son estrictamente internos.

Observa los siguientes ejemplos específicos de estas reglas en nuestro ejemplo:

  * `Aardvark` puede importar en cualquiera de `Bobcat`, `Cobra` o `Dingo`; sí importa `Bobcat` y `Cobra`.
  * `Bobcat` puede y efectivamente importa tanto `Cobra` como `Dingo`, que ambos tienen archivos de proyecto con UUIDs y están declarados como dependencias en la sección `[deps]` de `Bobcat`.
  * `Bobcat` no puede depender de `Aardvark` ya que `Aardvark` no tiene un archivo de proyecto.
  * `Cobra` puede y efectivamente importa `Dingo`, que tiene un archivo de proyecto y UUID, y está declarado como una dependencia en la sección `[deps]` de `Cobra`.
  * `Cobra` no puede depender de `Aardvark` o `Bobcat` ya que ninguno tiene UUIDs reales.
  * `Dingo` no puede importar nada porque tiene un archivo de proyecto sin una sección `[deps]`.

**El mapa de rutas** en un directorio de paquete es simple: mapea los nombres de subdirectorios a sus correspondientes rutas de punto de entrada. En otras palabras, si la ruta a nuestro directorio de ejemplo es `/home/me/animals`, entonces el mapa `paths` podría ser representado por este diccionario:

```julia
paths = Dict(
    (UUID("00000000-0000-0000-0000-000000000000"), :Aardvark) =>
        "/home/me/AnimalPackages/Aardvark/src/Aardvark.jl",
    (UUID("85ad11c7-31f6-5d08-84db-0a4914d4cadf"), :Bobcat) =>
        "/home/me/AnimalPackages/Bobcat/src/Bobcat.jl",
    (UUID("4725e24d-f727-424b-bca0-c4307a3456fa"), :Cobra) =>
        "/home/me/AnimalPackages/Cobra/src/Cobra.jl",
    (UUID("7a7925be-828c-4418-bbeb-bac8dfc843bc"), :Dingo) =>
        "/home/me/AnimalPackages/Dingo/src/Dingo.jl",
)
```

Dado que todos los paquetes en un entorno de directorio de paquetes son, por definición, subdirectorios con los archivos de punto de entrada esperados, sus entradas de mapa `paths` siempre tienen esta forma.

### Environment stacks

El tercer y último tipo de entorno es uno que combina otros entornos superponiendo varios de ellos, haciendo que los paquetes en cada uno estén disponibles en un único entorno compuesto. Estos entornos compuestos se llaman *pilas de entornos*. La variable global `LOAD_PATH` de Julia define una pila de entornos: el entorno en el que opera el proceso de Julia. Si deseas que tu proceso de Julia tenga acceso solo a los paquetes en un proyecto o directorio de paquetes, haz que sea la única entrada en `LOAD_PATH`. Sin embargo, a menudo es bastante útil tener acceso a algunas de tus herramientas favoritas: bibliotecas estándar, perfiles, depuradores, utilidades personales, etc.—incluso si no son dependencias del proyecto en el que estás trabajando. Al agregar un entorno que contenga estas herramientas a la ruta de carga, inmediatamente tienes acceso a ellas en el código de nivel superior sin necesidad de agregarlas a tu proyecto.

El mecanismo para combinar las raíces, el gráfico y las estructuras de datos de caminos de los componentes de una pila de entornos es simple: se fusionan como diccionarios, favoreciendo las entradas anteriores sobre las posteriores en caso de colisiones de claves. En otras palabras, si tenemos `stack = [env₁, env₂, …]` entonces tenemos:

```julia
roots = reduce(merge, reverse([roots₁, roots₂, …]))
graph = reduce(merge, reverse([graph₁, graph₂, …]))
paths = reduce(merge, reverse([paths₁, paths₂, …]))
```

Las variables subscriptadas `rootsᵢ`, `graphᵢ` y `pathsᵢ` corresponden a los entornos subscriptados `envᵢ`, contenidos en `stack`. El `reverse` está presente porque `merge` favorece el último argumento en lugar del primero cuando hay colisiones entre las claves en sus diccionarios de argumentos. Hay un par de características notables de este diseño:

1. El *entorno primario*—es decir, el primer entorno en una pila—está fielmente incrustado en un entorno apilado. Se garantiza que el gráfico de dependencias completo del primer entorno en una pila se incluya intacto en el entorno apilado, incluyendo las mismas versiones de todas las dependencias.
2. Los paquetes en entornos no primarios pueden terminar utilizando versiones incompatibles de sus dependencias, incluso si sus propios entornos son completamente compatibles. Esto puede suceder cuando una de sus dependencias es oscurecida por una versión en un entorno anterior en la pila (ya sea por gráfico o por ruta, o ambos).

Dado que el entorno principal es típicamente el entorno de un proyecto en el que estás trabajando, mientras que los entornos más adelante en la pila contienen herramientas adicionales, este es el compromiso correcto: es mejor romper tus herramientas de desarrollo pero mantener el proyecto funcionando. Cuando ocurren tales incompatibilidades, normalmente querrás actualizar tus herramientas de desarrollo a versiones que sean compatibles con el proyecto principal.

### [Package Extensions](@id man-extensions)

Un paquete "extensión" es un módulo que se carga automáticamente cuando un conjunto específico de otros paquetes (sus "disparadores") se cargan en la sesión actual de Julia. Las extensiones se definen en la sección `[extensions]` del archivo del proyecto. Los disparadores de una extensión son un subconjunto de esos paquetes listados en la sección `[weakdeps]` (y posiblemente, aunque poco común, en la sección `[deps]`) del archivo del proyecto. Esos paquetes pueden tener entradas de compatibilidad como otros paquetes.

```toml
name = "MyPackage"

[compat]
ExtDep = "1.0"
OtherExtDep = "1.0"

[weakdeps]
ExtDep = "c9a23..." # uuid
OtherExtDep = "862e..." # uuid

[extensions]
BarExt = ["ExtDep", "OtherExtDep"]
FooExt = "ExtDep"
...
```

Las claves bajo `extensions` son los nombres de las extensiones. Se cargan cuando se cargan todos los paquetes en el lado derecho (los disparadores) de esa extensión. Si una extensión solo tiene un disparador, la lista de disparadores se puede escribir como una sola cadena por brevedad. La ubicación del punto de entrada de la extensión está en `ext/FooExt.jl` o `ext/FooExt/FooExt.jl` para la extensión `FooExt`. El contenido de una extensión a menudo está estructurado como:

```
module FooExt

# Load main package and triggers
using MyPackage, ExtDep

# Extend functionality in main package with types from the triggers
MyPackage.func(x::ExtDep.SomeStruct) = ...

end
```

Cuando se agrega un paquete con extensiones a un entorno, las secciones `weakdeps` y `extensions` se almacenan en el archivo de manifiesto en la sección de ese paquete. Las reglas de búsqueda de dependencias para un paquete son las mismas que para su "padre", excepto que los desencadenantes listados también se consideran como dependencias.

### [Package/Environment Preferences](@id preferences)

Las preferencias son diccionarios de metadatos que influyen en el comportamiento del paquete dentro de un entorno. El sistema de preferencias admite la lectura de preferencias en tiempo de compilación, lo que significa que, en el momento de cargar el código, debemos asegurarnos de que los archivos de precompilación seleccionados por Julia se construyeron con las mismas preferencias que el entorno actual antes de cargarlos. La API pública para modificar las preferencias se encuentra dentro del paquete [Preferences.jl](https://github.com/JuliaPackaging/Preferences.jl). Las preferencias se almacenan como diccionarios TOML dentro de un archivo `(Julia)LocalPreferences.toml` junto al proyecto actualmente activo. Si una preferencia es "exportada", se almacena en el `(Julia)Project.toml` en su lugar. La intención es permitir que los proyectos compartidos contengan preferencias compartidas, mientras se permite a los usuarios anular esas preferencias con sus propias configuraciones en el archivo LocalPreferences.toml, que debería estar .gitignored como su nombre implica.

Las preferencias que se acceden durante la compilación se marcan automáticamente como preferencias en tiempo de compilación, y cualquier cambio registrado en estas preferencias provocará que el compilador de Julia recompile cualquier archivo(s) de precompilación en caché (`.ji` y los correspondientes archivos `.so`, `.dll` o `.dylib`) para ese módulo. Esto se hace serializando el hash de todas las preferencias en tiempo de compilación durante la compilación, y luego verificando ese hash contra el entorno actual al buscar el(los) archivo(s) adecuados para cargar.

Las preferencias se pueden establecer con valores predeterminados a nivel de depósito; si el paquete Foo está instalado en tu entorno global y tiene preferencias establecidas, estas preferencias se aplicarán siempre que tu entorno global sea parte de tu `LOAD_PATH`. Las preferencias en entornos más altos en la pila de entornos son anuladas por las entradas más cercanas en la ruta de carga, terminando con el proyecto actualmente activo. Esto permite que existan valores predeterminados de preferencias a nivel de depósito, con proyectos activos que pueden fusionar o incluso sobrescribir completamente estas preferencias heredadas. Consulta la cadena de documentación para `Preferences.set_preferences!()` para obtener todos los detalles sobre cómo establecer preferencias para permitir o deshabilitar la fusión.

## Conclusion

La gestión de paquetes federados y la reproducibilidad precisa del software son objetivos difíciles pero valiosos en un sistema de paquetes. En combinación, estos objetivos conducen a un mecanismo de carga de paquetes más complejo que el que tienen la mayoría de los lenguajes dinámicos, pero también ofrecen escalabilidad y reproducibilidad que se asocian más comúnmente con los lenguajes estáticos. Típicamente, los usuarios de Julia deberían poder utilizar el gestor de paquetes integrado para gestionar sus proyectos sin necesidad de una comprensión precisa de estas interacciones. Una llamada a `Pkg.add("X")` añadirá a los archivos de proyecto y manifiesto apropiados, seleccionados a través de `Pkg.activate("Y")`, de modo que una llamada futura a `import X` cargará `X` sin más consideración.
