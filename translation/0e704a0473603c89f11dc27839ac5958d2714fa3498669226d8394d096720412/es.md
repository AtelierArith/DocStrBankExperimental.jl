```
as
```

`as` se utiliza como una palabra clave para renombrar un identificador traído al ámbito por `import` o `using`, con el propósito de evitar conflictos de nombres así como para acortar nombres.  (Fuera de las declaraciones `import` o `using`, `as` no es una palabra clave y puede ser utilizado como un identificador ordinario.)

`import LinearAlgebra as LA` trae la biblioteca estándar `LinearAlgebra` importada al ámbito como `LA`.

`import LinearAlgebra: eigen as eig, cholesky as chol` trae los métodos `eigen` y `cholesky` de `LinearAlgebra` al ámbito como `eig` y `chol` respectivamente.

`as` funciona con `using` solo cuando se traen identificadores individuales al ámbito. Por ejemplo, `using LinearAlgebra: eigen as eig` o `using LinearAlgebra: eigen as eig, cholesky as chol` funciona, pero `using LinearAlgebra as LA` es una sintaxis inválida, ya que no tiene sentido renombrar *todos* los nombres exportados de `LinearAlgebra` a `LA`.
