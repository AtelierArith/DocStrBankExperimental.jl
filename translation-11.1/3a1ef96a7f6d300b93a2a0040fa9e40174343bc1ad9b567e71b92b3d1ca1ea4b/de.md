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

Just as text output is performed by [`print`](@ref) und benutzerdefinierte Typen ihre textuelle Darstellung durch Überladen von [`show`](@ref) anzeigen können, bietet Julia einen standardisierten Mechanismus für reichhaltige Multimedia-Ausgaben (wie Bilder, formatierter Text oder sogar Audio und Video), der aus drei Teilen besteht:

  * Eine Funktion [`display(x)`](@ref), um die reichhaltigste verfügbare Multimedia-Darstellung eines Julia-Objekts `x` (mit einem Fallback in Klartext) anzufordern.
  * Die Überladung von [`show`](@ref) ermöglicht es, beliebige Multimedia-Darstellungen (gekennzeichnet durch standardisierte MIME-Typen) von benutzerdefinierten Typen anzugeben.
  * Multimedia-fähige Anzeige-Backends können registriert werden, indem man einen generischen [`AbstractDisplay`](@ref)-Typ unterklassen und sie über [`pushdisplay`](@ref) auf einen Stapel von Anzeige-Backends schiebt.

Die grundlegende Julia-Laufzeit bietet nur die Anzeige von reinem Text, aber reichhaltigere Anzeigen können aktiviert werden, indem externe Module geladen oder grafische Julia-Umgebungen (wie das auf IPython basierende IJulia-Notebook) verwendet werden.

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

Wie oben erwähnt, kann man auch neue Anzeige-Backends definieren. Zum Beispiel kann ein Modul, das PNG-Bilder in einem Fenster anzeigen kann, diese Fähigkeit bei Julia registrieren, sodass der Aufruf [`display(x)`](@ref) für Typen mit PNG-Darstellungen das Bild automatisch im Fenster des Moduls anzeigt.

Um einen neuen Anzeige-Backend zu definieren, sollte man zunächst einen Untertyp `D` der abstrakten Klasse [`AbstractDisplay`](@ref) erstellen. Dann sollte man für jeden MIME-Typ (`mime`-String), der auf `D` angezeigt werden kann, eine Funktion `display(d::D, ::MIME"mime", x) = ...` definieren, die `x` als diesen MIME-Typ anzeigt, normalerweise durch Aufruf von [`show(io, mime, x)`](@ref) oder [`repr(io, mime, x)`](@ref). Eine [`MethodError`](@ref) sollte ausgelöst werden, wenn `x` nicht als dieser MIME-Typ angezeigt werden kann; dies geschieht automatisch, wenn man `show` oder `repr` aufruft. Schließlich sollte man eine Funktion `display(d::D, x)` definieren, die [`showable(mime, x)`](@ref) nach den von `D` unterstützten `mime`-Typen abfragt und den "besten" anzeigt; ein `MethodError` sollte ausgelöst werden, wenn keine unterstützten MIME-Typen für `x` gefunden werden. Ebenso möchten einige Untertypen möglicherweise [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay) überschreiben. (Wiederum sollte man `import Base.display` verwenden, um neue Methoden zu `display` hinzuzufügen.) Die Rückgabewerte dieser Funktionen liegen in der Verantwortung der Implementierung (da es in einigen Fällen nützlich sein kann, einen Anzeige-"Handle" eines Typs zurückzugeben). Die Anzeige-Funktionen für `D` können dann direkt aufgerufen werden, aber sie können auch automatisch von [`display(x)`](@ref) aufgerufen werden, indem einfach ein neues Display auf den Anzeige-Backend-Stack geschoben wird mit:

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
