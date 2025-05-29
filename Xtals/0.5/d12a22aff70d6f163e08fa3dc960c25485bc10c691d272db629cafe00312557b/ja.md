```
atoms = read_xyz("molecule.xyz")
```

.xyzファイルから原子種のリストとそれに対応する座標を読み込みます。

# 引数

  * `filename::AbstractString`: .xyzファイルのパスとファイル名

# 戻り値

  * `atoms::Atoms{Cart}`: .xyzファイルから読み込まれた原子の集合。
