```
credential_callback(...) -> Cint
```

Una función de callback de credenciales de LibGit2 que proporciona diferentes funcionalidades de adquisición de credenciales con respecto a un protocolo de conexión. El `payload_ptr` debe contener un objeto `LibGit2.CredentialPayload` que mantendrá el seguimiento del estado y la configuración.

El `allowed_types` contiene una máscara de bits de valores `LibGit2.Consts.GIT_CREDTYPE` que especifican qué métodos de autenticación deben intentarse.

La autenticación de credenciales se realiza en el siguiente orden (si es compatible):

  * Agente SSH
  * Par de claves privadas/públicas SSH
  * Nombre de usuario/contraseña en texto plano

Si se presenta a un usuario un aviso de credenciales, puede abortar el aviso escribiendo `^D` (presionando la tecla de control junto con la tecla `d`).

**Nota**: Debido a las especificidades del procedimiento de autenticación de `libgit2`, cuando la autenticación falla, esta función se llama nuevamente sin ninguna indicación de si la autenticación fue exitosa o no. Para evitar un bucle infinito al usar repetidamente las mismas credenciales defectuosas, mantendremos un seguimiento del estado utilizando el payload.

Para más detalles, consulte la guía de LibGit2 sobre [autenticación contra un servidor](https://libgit2.org/docs/guides/authentication/).
