```
macro
```

`macro` define un método para insertar código generado en un programa. Un macro mapea una secuencia de expresiones de argumento a una expresión devuelta, y la expresión resultante se sustituye directamente en el programa en el punto donde se invoca el macro. Los macros son una forma de ejecutar código generado sin llamar a [`eval`](@ref Main.eval), ya que el código generado simplemente se convierte en parte del programa circundante. Los argumentos de los macros pueden incluir expresiones, valores literales y símbolos. Los macros se pueden definir para un número variable de argumentos (varargs), pero no aceptan argumentos de palabra clave. Cada macro también recibe implícitamente los argumentos `__source__`, que contiene el número de línea y el nombre del archivo desde el cual se llama al macro, y `__module__`, que es el módulo en el que se expande el macro.

Consulta la sección del manual sobre [Metaprogramación](@ref) para obtener más información sobre cómo escribir un macro.

# Ejemplos

```jldoctest
julia> macro sayhello(name)
           return :( println("Hello, ", $name, "!") )
       end
@sayhello (macro with 1 method)

julia> @sayhello "Charlie"
Hello, Charlie!

julia> macro saylots(x...)
           return :( println("Say: ", $(x...)) )
       end
@saylots (macro with 1 method)

julia> @saylots "hey " "there " "friend"
Say: hey there friend
```
