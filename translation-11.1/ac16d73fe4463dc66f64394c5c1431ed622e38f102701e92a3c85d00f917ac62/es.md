# Running External Programs

Julia toma la notación de comillas invertidas para comandos del shell, Perl y Ruby. Sin embargo, en Julia, escribir

```jldoctest
julia> `echo hello`
`echo hello`
```

difiere en varios aspectos del comportamiento en varios shells, Perl o Ruby:

  * En lugar de ejecutar inmediatamente el comando, las comillas invertidas crean un [`Cmd`](@ref) objeto para representar el comando. Puedes usar este objeto para conectar el comando a otros a través de tuberías, [`run`](@ref) lo, y [`read`](@ref) o [`write`](@ref) a él.
  * Cuando se ejecuta el comando, Julia no captura su salida a menos que lo organices específicamente para hacerlo. En su lugar, la salida del comando por defecto va a [`stdout`](@ref) como lo haría utilizando la llamada `system` de `libc`.
  * El comando nunca se ejecuta con un shell. En su lugar, Julia analiza la sintaxis del comando directamente, interpolando variables de manera apropiada y dividiendo en palabras como lo haría el shell, respetando la sintaxis de comillas del shell. El comando se ejecuta como un proceso hijo inmediato de `julia`, utilizando llamadas a `fork` y `exec`.

!!! note
    Lo siguiente asume un entorno Posix como en Linux o MacOS. En Windows, muchos comandos similares, como `echo` y `dir`, no son programas externos y en su lugar están integrados en el shell `cmd.exe` mismo. Una opción para ejecutar estos comandos es invocar `cmd.exe`, por ejemplo `cmd /C echo hello`. Alternativamente, Julia se puede ejecutar dentro de un entorno Posix como Cygwin.


Aquí hay un ejemplo simple de ejecutar un programa externo:

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

El `hello` es la salida del comando `echo`, enviado a [`stdout`](@ref). Si el comando externo no se ejecuta correctamente, el método run lanza un [`ProcessFailedException`](@ref).

Si deseas leer la salida del comando externo, [`read`](@ref) o [`readchomp`](@ref) se puede usar en su lugar:

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

Más generalmente, puedes usar [`open`](@ref) para leer o escribir en un comando externo.

```jldoctest
julia> open(`less`, "w", stdout) do io
           for i = 1:3
               println(io, i)
           end
       end
1
2
3
```

El nombre del programa y los argumentos individuales en un comando se pueden acceder e iterar como si el comando fuera un arreglo de cadenas:

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

Supongamos que quieres hacer algo un poco más complicado y usar el nombre de un archivo en la variable `file` como un argumento para un comando. Puedes usar `$` para la interpolación de la misma manera que lo harías en un literal de cadena (ver [Strings](@ref)):

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

Una trampa común al ejecutar programas externos a través de un shell es que si un nombre de archivo contiene caracteres que son especiales para el shell, pueden causar un comportamiento indeseable. Supongamos, por ejemplo, que en lugar de `/etc/passwd`, queremos ordenar el contenido del archivo `/Volumes/External HD/data.csv`. Intentémoslo:

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

¿Cómo se citó el nombre del archivo? Julia sabe que `file` se debe interpolar como un solo argumento, por lo que cita la palabra por ti. En realidad, eso no es del todo exacto: el valor de `file` nunca es interpretado por un shell, por lo que no hay necesidad de citas reales; las citas se insertan solo para la presentación al usuario. Esto incluso funcionará si interpolas un valor como parte de una palabra de shell:

```jldoctest
julia> path = "/Volumes/External HD"
"/Volumes/External HD"

julia> name = "data"
"data"

julia> ext = "csv"
"csv"

julia> `sort $path/$name.$ext`
`sort '/Volumes/External HD/data.csv'`
```

Como puedes ver, el espacio en la variable `path` está correctamente escapado. Pero, ¿qué pasa si *quieres* interpolar múltiples palabras? En ese caso, simplemente usa un array (o cualquier otro contenedor iterable):

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

Si interpolas un array como parte de una palabra de shell, Julia emula la generación de argumentos `{a,b,c}` del shell:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

Además, si interpolas múltiples arreglos en la misma palabra, se emula el comportamiento de generación del producto cartesiano del shell:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> exts = ["aux","log"]
2-element Vector{String}:
 "aux"
 "log"

julia> `rm -f $names.$exts`
`rm -f foo.aux foo.log bar.aux bar.log baz.aux baz.log`
```

Dado que puedes interpolar arreglos literales, puedes utilizar esta funcionalidad generativa sin necesidad de crear primero objetos de arreglo temporales:

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

Inevitable, uno quiere escribir comandos que no son tan simples, y se vuelve necesario usar comillas. Aquí hay un ejemplo simple de un one-liner de Perl en un aviso de shell:

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

La expresión de Perl necesita estar entre comillas simples por dos razones: para que los espacios no dividan la expresión en múltiples palabras de shell, y para que el uso de variables de Perl como `$|` (sí, ese es el nombre de una variable en Perl) no cause interpolación. En otros casos, es posible que desees usar comillas dobles para que la interpolación *sí* ocurra:

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

En general, la sintaxis de comillas invertidas de Julia está cuidadosamente diseñada para que puedas simplemente cortar y pegar comandos de shell tal como están en comillas invertidas y funcionarán: el escape, la citación y los comportamientos de interpolación son los mismos que los del shell. La única diferencia es que la interpolación está integrada y es consciente de la noción de Julia sobre lo que es un único valor de cadena y lo que es un contenedor para múltiples valores. Intentemos los dos ejemplos anteriores en Julia:

```jldoctest
julia> A = `perl -le '$|=1; for (0..3) { print }'`
`perl -le '$|=1; for (0..3) { print }'`

julia> run(A);
0
1
2
3

julia> first = "A"; second = "B";

julia> B = `perl -le 'print for @ARGV' "1: $first" "2: $second"`
`perl -le 'print for @ARGV' '1: A' '2: B'`

julia> run(B);
1: A
2: B
```

Los resultados son idénticos, y el comportamiento de interpolación de Julia imita el de la shell con algunas mejoras debido al hecho de que Julia admite objetos iterables de primera clase, mientras que la mayoría de las shells utilizan cadenas divididas por espacios para esto, lo que introduce ambigüedades. Al intentar portar comandos de shell a Julia, intenta copiar y pegar primero. Dado que Julia te muestra los comandos antes de ejecutarlos, puedes examinar fácilmente y de forma segura su interpretación sin causar ningún daño.

## Pipelines

Los metacaracteres de shell, como `|`, `&` y `>`, deben ser citados (o escapados) dentro de los backticks de Julia:

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

Esta expresión invoca el comando `echo` con tres palabras como argumentos: `hello`, `|` y `sort`. El resultado es que se imprime una sola línea: `hello | sort`. ¿Cómo, entonces, se construye una tubería? En lugar de usar `'|'` dentro de comillas invertidas, se utiliza [`pipeline`](@ref):

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

Esto envía la salida del comando `echo` al comando `sort`. Por supuesto, esto no es muy interesante ya que solo hay una línea para ordenar, pero ciertamente podemos hacer cosas mucho más interesantes:

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

Esto imprime los cinco IDs de usuario más altos en un sistema UNIX. Los comandos `cut`, `sort` y `tail` se generan como hijos inmediatos del proceso `julia` actual, sin un proceso de shell intermedio. Julia misma realiza el trabajo de configurar tuberías y conectar descriptores de archivos que normalmente hace el shell. Dado que Julia hace esto por sí misma, mantiene un mejor control y puede hacer algunas cosas que los shells no pueden.

Julia puede ejecutar múltiples comandos en paralelo:

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

El orden de la salida aquí es no determinista porque los dos procesos `echo` se inician casi simultáneamente y compiten por hacer la primera escritura en el descriptor [`stdout`](@ref) que comparten entre sí y con el proceso padre `julia`. Julia te permite canalizar la salida de ambos procesos a otro programa:

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

En términos de plomería de UNIX, lo que está sucediendo aquí es que se crea un único objeto de tubería de UNIX y se escribe en él por ambos procesos `echo`, y el otro extremo de la tubería es leído por el comando `sort`.

La redirección de IO se puede lograr pasando argumentos de palabra clave `stdin`, `stdout` y `stderr` a la función `pipeline`:

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

Al leer y escribir en ambos extremos de un pipeline desde un solo proceso, es importante evitar forzar al kernel a almacenar en búfer todos los datos.

Por ejemplo, al leer toda la salida de un comando, llama a `read(out, String)`, no a `wait(process)`, ya que el primero consumirá activamente todos los datos escritos por el proceso, mientras que el segundo intentará almacenar los datos en los búferes del kernel mientras espera que se conecte un lector.

Otra solución común es separar el lector y el escritor del pipeline en [`Task`](@ref)s separados:

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

(comúnmente también, el lector no es una tarea separada, ya que inmediatamente `fetch` lo obtenemos de todos modos).

### Complex Example

La combinación de un lenguaje de programación de alto nivel, una abstracción de comando de primera clase y la configuración automática de tuberías entre procesos es poderosa. Para dar una idea de los complejos pipelines que se pueden crear fácilmente, aquí hay algunos ejemplos más sofisticados, con disculpas por el uso excesivo de líneas de Perl:

```jldoctest prefixer; filter = r"([A-B] [0-5])"
julia> prefixer(prefix, sleep) = `perl -nle '$|=1; print "'$prefix' ", $_; sleep '$sleep';'`;

julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`, prefixer("A",2) & prefixer("B",2)));
B 0
A 1
B 2
A 3
B 4
A 5
```

Este es un ejemplo clásico de un único productor alimentando a dos consumidores concurrentes: un proceso `perl` genera líneas con los números del 0 al 5, mientras que dos procesos paralelos consumen esa salida, uno prefijando las líneas con la letra "A" y el otro con la letra "B". Qué consumidor recibe la primera línea es no determinístico, pero una vez que esa carrera ha sido ganada, las líneas son consumidas alternativamente por un proceso y luego por el otro. (Configurar `$|=1` en Perl hace que cada declaración de impresión vacíe el [`stdout`](@ref) handle, lo cual es necesario para que este ejemplo funcione. De lo contrario, toda la salida se almacena en búfer y se imprime en el tubo a la vez, para ser leída por solo un proceso consumidor.)

Aquí hay un ejemplo aún más complejo de productor-consumidor de múltiples etapas:

```jldoctest prefixer; filter = r"[A-B] [X-Z] [0-5]"
julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`,
           prefixer("X",3) & prefixer("Y",3) & prefixer("Z",3),
           prefixer("A",2) & prefixer("B",2)));
A X 0
B Y 1
A Z 2
B X 3
A Y 4
B Z 5
```

Este ejemplo es similar al anterior, excepto que hay dos etapas de consumidores, y las etapas tienen diferentes latencias, por lo que utilizan un número diferente de trabajadores en paralelo, para mantener un rendimiento saturado.

Te animamos a que pruebes todos estos ejemplos para ver cómo funcionan.

## `Cmd` Objects

La sintaxis de comillas invertidas crea un objeto del tipo [`Cmd`](@ref). Tal objeto también puede ser construido directamente a partir de un `Cmd` existente o una lista de argumentos:

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

Esto te permite especificar varios aspectos del entorno de ejecución del `Cmd` a través de argumentos de palabra clave. Por ejemplo, la palabra clave `dir` proporciona control sobre el directorio de trabajo del `Cmd`:

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

Y la palabra clave `env` te permite establecer variables de entorno de ejecución:

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

Consulta [`Cmd`](@ref) para obtener argumentos clave adicionales. Los comandos [`setenv`](@ref) y [`addenv`](@ref) proporcionan otro medio para reemplazar o agregar a las variables de entorno de ejecución de `Cmd`, respectivamente:

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
