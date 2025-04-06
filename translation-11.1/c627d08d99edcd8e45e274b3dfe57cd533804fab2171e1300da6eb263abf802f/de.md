```
credential_callback(...) -> Cint
```

Eine LibGit2-Anmeldeinformationen-Callback-Funktion, die unterschiedliche Funktionen zur Beschaffung von Anmeldeinformationen in Bezug auf ein Verbindungsprotokoll bereitstellt. Der `payload_ptr` muss ein `LibGit2.CredentialPayload`-Objekt enthalten, das den Zustand und die Einstellungen verfolgt.

Die `allowed_types` enthält eine Bitmaske von `LibGit2.Consts.GIT_CREDTYPE`-Werten, die angeben, welche Authentifizierungsmethoden versucht werden sollen.

Die Authentifizierung der Anmeldeinformationen erfolgt in der folgenden Reihenfolge (sofern unterstützt):

  * SSH-Agent
  * SSH-Privat-/Öffenschlüssel-Paar
  * Benutzername/Passwort im Klartext

Wenn ein Benutzer mit einer Eingabeaufforderung für Anmeldeinformationen konfrontiert wird, kann er die Eingabeaufforderung abbrechen, indem er `^D` eingibt (die Steuerungstaste zusammen mit der `d`-Taste drückt).

**Hinweis**: Aufgrund der Besonderheiten des Authentifizierungsverfahrens von `libgit2` wird diese Funktion erneut aufgerufen, wenn die Authentifizierung fehlschlägt, ohne dass angezeigt wird, ob die Authentifizierung erfolgreich war oder nicht. Um eine Endlosschleife zu vermeiden, die durch die wiederholte Verwendung der gleichen fehlerhaften Anmeldeinformationen verursacht wird, werden wir den Zustand mithilfe des Payloads verfolgen.

Für weitere Details siehe den LibGit2-Leitfaden zum [Authentifizieren gegen einen Server](https://libgit2.org/docs/guides/authentication/).
