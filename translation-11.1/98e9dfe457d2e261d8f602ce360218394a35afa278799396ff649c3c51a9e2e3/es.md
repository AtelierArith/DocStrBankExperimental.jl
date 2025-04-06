```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

Imprime `xs` en un color especificado como un símbolo o un entero, opcionalmente en negrita.

La palabra clave `color` puede tomar cualquiera de los valores `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white`, o  `:yellow` o un entero entre 0 y 255 inclusive. Ten en cuenta que no todos los terminales soportan 256 colores.

Las palabras clave `bold=true`, `italic=true`, `underline=true`, `blink=true` son autoexplicativas. La palabra clave `reverse=true` imprime con los colores de primer plano y fondo intercambiados, y `hidden=true` debería ser invisible en el terminal pero aún puede ser copiado. Estas propiedades pueden ser utilizadas en cualquier combinación.

Consulta también [`print`](@ref), [`println`](@ref), [`show`](@ref).

!!! nota
    No todos los terminales soportan salida en cursiva. Algunos terminales interpretan la cursiva como reversa o parpadeo.


!!! compat "Julia 1.7"
    Las palabras clave excepto `color` y `bold` fueron añadidas en Julia 1.7.


!!! compat "Julia 1.10"
    El soporte para salida en cursiva fue añadido en Julia 1.10.

