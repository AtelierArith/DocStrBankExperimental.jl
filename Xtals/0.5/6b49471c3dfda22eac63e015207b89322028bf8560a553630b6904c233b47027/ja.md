```
translate_by!(coords, dx)
translate_by!(coords, dx, box)
translate_by!(molecule, dx)
translate_by!(molecule, dx, box)
```

ベクトル `dx` によって `coords` を移動します。つまり、ベクトル `dx` を加えます。

これは、`Frac` と `Cart` の座標の任意の組み合わせに対して機能します。

座標はその場で修正されます。

`Frac` と `Cart` の座標を混合する場合、`box` が必要です。

周期境界条件はここでは*適用されません*。

`molecule::Molecule` に適用されると、原子、電荷、および質量中心の座標がすべて移動されます。
