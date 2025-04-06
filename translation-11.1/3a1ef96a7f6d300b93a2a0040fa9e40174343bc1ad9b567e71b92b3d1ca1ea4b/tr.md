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

Tam metin çıktısı [`print`](@ref) ile gerçekleştirilirken ve kullanıcı tanımlı türler, metinsel temsilini aşırı yükleyerek belirtebiliyorken [`show`](@ref), Julia zengin multimedya çıktısı (görüntüler, biçimlendirilmiş metin veya hatta ses ve video gibi) için standartlaştırılmış bir mekanizma sağlar ve bu üç bölümden oluşur:

  * Bir [`display(x)`](@ref) fonksiyonu, bir Julia nesnesi `x` için en zengin mevcut çoklu ortam görüntüsünü (düz metin yedeği ile birlikte) talep etmek için kullanılır.
  * [`show`](@ref) aşırı yüklenmesi, kullanıcı tanımlı türlerin standart MIME türleriyle anahtarlanan keyfi çoklu ortam temsillerini belirtmeye olanak tanır.
  * Multimedya özellikli ekran arka uçları, genel bir [`AbstractDisplay`](@ref) türünü alt sınıflandırarak kaydedilebilir ve bunlar, [`pushdisplay`](@ref) aracılığıyla ekran arka uçları yığınına eklenebilir.

Temel Julia çalışma zamanı yalnızca düz metin görüntüleme sağlar, ancak daha zengin görüntülemeler, harici modüller yüklenerek veya grafiksel Julia ortamları (örneğin, IPython tabanlı IJulia defteri) kullanılarak etkinleştirilebilir.

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

Yukarıda belirtildiği gibi, yeni görüntü arka uçları da tanımlanabilir. Örneğin, bir modül bir pencerede PNG görüntüleri gösterebiliyorsa, bu yeteneği Julia ile kaydedebilir, böylece PNG temsilleri olan türler üzerinde [`display(x)`](@ref) çağrıldığında, görüntü otomatik olarak modülün penceresi kullanılarak gösterilecektir.

Yeni bir görüntüleme arka ucu tanımlamak için, önce [`AbstractDisplay`](@ref) soyut sınıfının bir alt türü `D` oluşturulmalıdır. Ardından, `D` üzerinde görüntülenebilecek her MIME türü (`mime` dizesi) için, `display(d::D, ::MIME"mime", x) = ...` şeklinde bir fonksiyon tanımlanmalıdır; bu fonksiyon genellikle [`show(io, mime, x)`](@ref) veya [`repr(io, mime, x)`](@ref) çağrılarak `x`'i o MIME türü olarak görüntüler. Eğer `x` o MIME türü olarak görüntülenemiyorsa, bir [`MethodError`](@ref) fırlatılmalıdır; bu, `show` veya `repr` çağrıldığında otomatik olarak gerçekleşir. Son olarak, `display(d::D, x)` fonksiyonu tanımlanmalı ve `D` tarafından desteklenen `mime` türlerini sorgulamak için [`showable(mime, x)`](@ref) çağrılmalı ve "en iyi" olanı görüntülenmelidir; `x` için desteklenen MIME türleri bulunamazsa bir `MethodError` fırlatılmalıdır. Benzer şekilde, bazı alt türler [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay)'ı geçersiz kılmak isteyebilir. (Yine, yeni yöntemler eklemek için `import Base.display` yapılmalıdır.) Bu fonksiyonların dönüş değerleri uygulamaya bağlıdır (çünkü bazı durumlarda belirli bir türde bir görüntüleme "handle" döndürmek faydalı olabilir). `D` için görüntüleme fonksiyonları doğrudan çağrılabilir, ancak görüntüleme-arka ucu yığınına yeni bir görüntüleme ekleyerek [`display(x)`](@ref)'dan otomatik olarak da çağrılabilir:

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
