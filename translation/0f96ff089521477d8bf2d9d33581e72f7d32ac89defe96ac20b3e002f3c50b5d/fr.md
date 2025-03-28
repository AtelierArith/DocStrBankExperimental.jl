```
Serialization.writeheader(s::AbstractSerializer)
```

Écrit un en-tête d'identification dans le sérialiseur spécifié. L'en-tête se compose de 8 octets comme suit :

| Décalage | Description                                        |
|:-------- |:-------------------------------------------------- |
| 0        | octet de balise (0x37)                             |
| 1-2      | octets de signature "JL"                           |
| 3        | version du protocole                               |
| 4        | bits 0-1 : ordre des octets : 0 = petit, 1 = grand |
| 4        | bits 2-3 : plateforme : 0 = 32 bits, 1 = 64 bits   |
| 5-7      | réservé                                            |
