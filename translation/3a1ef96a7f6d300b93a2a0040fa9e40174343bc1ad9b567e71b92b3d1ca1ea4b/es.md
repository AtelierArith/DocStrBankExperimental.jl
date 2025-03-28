# I/O and Network

## General I/O

```@docs
Base.stdout
Base.stderr
Base.stdin
Base.read(::AbstractString)
Base.write(::AbstractString, ::Any)
Base.open
Base.IOStream
Base.IOBuffer
Base.take!(::Base.GenericIOBuffer)
Base.Pipe
Base.link_pipe!
Base.fdio
Base.flush
Base.close
Base.closewrite
Base.write
Base.read
Base.read!
Base.readbytes!
Base.unsafe_read
Base.unsafe_write
Base.readeach
Base.peek
Base.position
Base.seek
Base.seekstart
Base.seekend
Base.skip
Base.mark
Base.unmark
Base.reset(::IO)
Base.ismarked
Base.eof
Base.isreadonly
Base.iswritable
Base.isreadable
Base.isexecutable
Base.isopen
Base.fd
Base.redirect_stdio
Base.redirect_stdout
Base.redirect_stdout(::Function, ::Any)
Base.redirect_stderr
Base.redirect_stderr(::Function, ::Any)
Base.redirect_stdin
Base.redirect_stdin(::Function, ::Any)
Base.readchomp
Base.truncate
Base.skipchars
Base.countlines
Base.PipeBuffer
Base.readavailable
Base.IOContext
Base.IOContext(::IO, ::Pair)
Base.IOContext(::IO, ::IOContext)
```

## Text I/O

```@docs
Base.show(::IO, ::Any)
Base.summary
Base.print
Base.println
Base.printstyled
Base.sprint
Base.showerror
Base.dump
Meta.@dump
Base.readline
Base.readuntil
Base.readlines
Base.eachline
Base.copyline
Base.copyuntil
Base.displaysize
```

## [Multimedia I/O](@id Multimedia-I/O)

Justo como la salida de texto se realiza mediante [`print`](@ref) y los tipos definidos por el usuario pueden indicar su representación textual sobrecargando [`show`](@ref), Julia proporciona un mecanismo estandarizado para la salida multimedia rica (como imágenes, texto formateado o incluso audio y video), que consta de tres partes:

  * Una función [`display(x)`](@ref) para solicitar la representación multimedia más rica disponible de un objeto Julia `x` (con un retroceso en texto plano).
  * Sobrecargar [`show`](@ref) permite indicar representaciones multimedia arbitrarias (identificadas por tipos MIME estándar) de tipos definidos por el usuario.
  * Los backends de visualización capaces de multimedia pueden ser registrados al subclasear un tipo genérico [`AbstractDisplay`](@ref) y empujándolos a una pila de backends de visualización a través de [`pushdisplay`](@ref).

El runtime base de Julia proporciona solo visualización en texto plano, pero se pueden habilitar visualizaciones más ricas cargando módulos externos o utilizando entornos gráficos de Julia (como el cuaderno IJulia basado en IPython).

```@docs
Base.AbstractDisplay
Base.Multimedia.display
Base.Multimedia.redisplay
Base.Multimedia.displayable
Base.show(::IO, ::Any, ::Any)
Base.Multimedia.showable
Base.repr(::MIME, ::Any)
Base.MIME
Base.@MIME_str
```

Como se mencionó anteriormente, también se pueden definir nuevos backends de visualización. Por ejemplo, un módulo que puede mostrar imágenes PNG en una ventana puede registrar esta capacidad con Julia, de modo que al llamar [`display(x)`](@ref) en tipos con representaciones PNG, la imagen se mostrará automáticamente utilizando la ventana del módulo.

Para definir un nuevo backend de visualización, primero se debe crear un subtipo `D` de la clase abstracta [`AbstractDisplay`](@ref). Luego, para cada tipo MIME (`mime` string) que se puede mostrar en `D`, se debe definir una función `display(d::D, ::MIME"mime", x) = ...` que muestre `x` como ese tipo MIME, generalmente llamando a [`show(io, mime, x)`](@ref) o [`repr(io, mime, x)`](@ref). Se debe lanzar un [`MethodError`](@ref) si `x` no se puede mostrar como ese tipo MIME; esto es automático si se llama a `show` o `repr`. Finalmente, se debe definir una función `display(d::D, x)` que consulte [`showable(mime, x)`](@ref) para los tipos `mime` soportados por `D` y muestre el "mejor"; se debe lanzar un `MethodError` si no se encuentran tipos MIME soportados para `x`. De manera similar, algunos subtipos pueden desear anular [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay). (Nuevamente, se debe `import Base.display` para agregar nuevos métodos a `display`.) Los valores de retorno de estas funciones dependen de la implementación (ya que en algunos casos puede ser útil devolver un "manejador" de visualización de algún tipo). Las funciones de visualización para `D` se pueden llamar directamente, pero también se pueden invocar automáticamente desde [`display(x)`](@ref) simplemente empujando una nueva visualización en la pila del backend de visualización con:

```@docs
Base.Multimedia.pushdisplay
Base.Multimedia.popdisplay
Base.Multimedia.TextDisplay
Base.Multimedia.istextmime
```

## Network I/O

```@docs
Base.bytesavailable
Base.ntoh
Base.hton
Base.ltoh
Base.htol
Base.ENDIAN_BOM
```
