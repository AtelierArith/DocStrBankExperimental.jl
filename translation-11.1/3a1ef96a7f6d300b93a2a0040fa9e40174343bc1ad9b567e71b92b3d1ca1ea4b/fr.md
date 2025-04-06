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

Tout comme la sortie de texte est effectuée par [`print`](@ref) et que les types définis par l'utilisateur peuvent indiquer leur représentation textuelle en surchargeant [`show`](@ref), Julia fournit un mécanisme standardisé pour la sortie multimédia riche (comme des images, du texte formaté, ou même de l'audio et de la vidéo), composé de trois parties :

  * Une fonction [`display(x)`](@ref) pour demander l'affichage multimédia le plus riche disponible d'un objet Julia `x` (avec un retour en texte brut).
  * Surcharge de [`show`](@ref) permet d'indiquer des représentations multimédias arbitraires (clés par des types MIME standard) de types définis par l'utilisateur.
  * Les backends d'affichage capables de multimédia peuvent être enregistrés en sous-classant un type générique [`AbstractDisplay`](@ref) et en les empilant sur une pile de backends d'affichage via [`pushdisplay`](@ref).

Le runtime de base de Julia ne fournit qu'un affichage en texte brut, mais des affichages plus riches peuvent être activés en chargeant des modules externes ou en utilisant des environnements graphiques Julia (comme le notebook IJulia basé sur IPython).

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

Comme mentionné ci-dessus, on peut également définir de nouveaux backends d'affichage. Par exemple, un module qui peut afficher des images PNG dans une fenêtre peut enregistrer cette capacité auprès de Julia, de sorte qu'appeler [`display(x)`](@ref) sur des types avec des représentations PNG affichera automatiquement l'image en utilisant la fenêtre du module.

Pour définir un nouveau backend d'affichage, il faut d'abord créer un sous-type `D` de la classe abstraite [`AbstractDisplay`](@ref). Ensuite, pour chaque type MIME (`mime` chaîne) qui peut être affiché sur `D`, il faut définir une fonction `display(d::D, ::MIME"mime", x) = ...` qui affiche `x` en tant que ce type MIME, généralement en appelant [`show(io, mime, x)`](@ref) ou [`repr(io, mime, x)`](@ref). Une [`MethodError`](@ref) doit être lancée si `x` ne peut pas être affiché en tant que ce type MIME ; cela est automatique si l'on appelle `show` ou `repr`. Enfin, il faut définir une fonction `display(d::D, x)` qui interroge [`showable(mime, x)`](@ref) pour les types `mime` pris en charge par `D` et affiche le "meilleur" ; une `MethodError` doit être lancée si aucun type MIME pris en charge n'est trouvé pour `x`. De même, certains sous-types peuvent souhaiter remplacer [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay). (Encore une fois, il faut `import Base.display` pour ajouter de nouvelles méthodes à `display`.) Les valeurs de retour de ces fonctions dépendent de l'implémentation (puisqu'il peut être utile dans certains cas de retourner un "handle" d'affichage de quelque type). Les fonctions d'affichage pour `D` peuvent alors être appelées directement, mais elles peuvent également être invoquées automatiquement depuis [`display(x)`](@ref) simplement en ajoutant un nouvel affichage à la pile de backend d'affichage avec :

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
