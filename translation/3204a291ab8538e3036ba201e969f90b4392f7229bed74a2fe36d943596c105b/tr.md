```
@__DIR__ -> String
```

Mevcut dizinin mutlak yolunu bir dize olarak elde etmek için makro.

Eğer bir betikte ise, `@__DIR__` makro çağrısını içeren betiğin dizinini döner. Eğer bir REPL'den çalıştırılırsa veya `julia -e <expr>` ile değerlendirilirse, mevcut çalışma dizinini döner.

# Örnekler

Örnek, `@__DIR__` ve `pwd()`'nin davranışlarındaki farkı, mevcut çalışma dizininden farklı bir dizinde basit bir betik oluşturarak ve her iki komutu da çalıştırarak gösterir:

```julia-repl
julia> cd("/home/JuliaUser") # çalışma dizini

julia> # /home/JuliaUser/Projects dizininde betik oluştur
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # betik dizinini ve mevcut çalışma dizinini çıktılar
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
