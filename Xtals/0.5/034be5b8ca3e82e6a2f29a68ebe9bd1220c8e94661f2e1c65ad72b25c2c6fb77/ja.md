```
nc = net_charge(charges)
nc = net_charge(crystal)
nc = net_charge(molecule)
```

`charges::Charges` または `crystal::Crystal` または `molecule::Molecule` の中の電荷の合計を求めます。（電荷がない場合、正味の電荷はゼロです。）
