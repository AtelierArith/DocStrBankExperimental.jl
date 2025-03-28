```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Stocker le `payload` d'identification pour une réutilisation lors d'une future authentification. Ne doit être appelé que lorsque l'authentification a réussi.

Le mot-clé `shred` contrôle si les informations sensibles dans le champ d'identification du payload doivent être détruites. Ne doit être défini sur `false` que lors des tests.
