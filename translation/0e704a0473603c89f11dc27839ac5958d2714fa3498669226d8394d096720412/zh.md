```
as
```

`as` 被用作关键字，以重命名通过 `import` 或 `using` 引入作用域的标识符，目的是为了处理名称冲突以及缩短名称。 （在 `import` 或 `using` 语句之外，`as` 不是关键字，可以作为普通标识符使用。）

`import LinearAlgebra as LA` 将导入的 `LinearAlgebra` 标准库引入作用域，命名为 `LA`。

`import LinearAlgebra: eigen as eig, cholesky as chol` 将 `LinearAlgebra` 中的 `eigen` 和 `cholesky` 方法引入作用域，分别命名为 `eig` 和 `chol`。

`as` 仅在单个标识符被引入作用域时与 `using` 一起使用。例如，`using LinearAlgebra: eigen as eig` 或 `using LinearAlgebra: eigen as eig, cholesky as chol` 是有效的，但 `using LinearAlgebra as LA` 是无效的语法，因为将 `LinearAlgebra` 中的 *所有* 导出名称重命名为 `LA` 是没有意义的。
