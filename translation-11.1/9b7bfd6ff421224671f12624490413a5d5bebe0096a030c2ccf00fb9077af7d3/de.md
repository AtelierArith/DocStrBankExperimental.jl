```
macro
```

`macro` definiert eine Methode zum Einfügen von generiertem Code in ein Programm. Ein Makro ordnet eine Sequenz von Argumentausdrücken einem zurückgegebenen Ausdruck zu, und der resultierende Ausdruck wird direkt an der Stelle in das Programm eingefügt, an der das Makro aufgerufen wird. Makros sind eine Möglichkeit, generierten Code auszuführen, ohne [`eval`](@ref Main.eval) aufzurufen, da der generierte Code stattdessen einfach Teil des umgebenden Programms wird. Makroargumente können Ausdrücke, literale Werte und Symbole enthalten. Makros können für eine variable Anzahl von Argumenten (varargs) definiert werden, akzeptieren jedoch keine Schlüsselwortargumente. Jedes Makro erhält auch implizit die Argumente `__source__`, die die Zeilennummer und den Dateinamen enthält, aus dem das Makro aufgerufen wird, und `__module__`, das das Modul ist, in dem das Makro erweitert wird.

Siehe den Abschnitt im Handbuch über [Metaprogrammierung](@ref) für weitere Informationen darüber, wie man ein Makro schreibt.

# Beispiele

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
