# Konfiguration OpenSSH Server
Die Konfiguration des SSH Server erfolgt durch Anpassen der Konfigurationsdatei, üblicherweise `/etc/ssh/sshd_config`.

Um die Anpassung der Konfiguration zu aktivieren, muss der SSH Server neu gestartet werden.


## Deaktivieren der Anmeldung als root
In der Standard Konfiguration erlauben viele SSH Server Installationen das Login von außen mit dem Benutzer `root`. Das macht Sinn für neu installierte Systeme, die nach der Installation eventuell noch gar keine anderen Benutzerkonten eingerichtet haben. Als erster Schritt sollte also ein Benutzerkonto angelegt werden.

Anschließend kann man den Zugang für `root` über die SSH sperren:

```no-highlight
PermitRootLogin no
```

## Einschränkung der erlaubten Benutzer
In der Standard Konfiguration kann sich jeder Benutzer, der auf dem entfernten System ein Konto hat, anmelden. Beliebtes Angriffsziel sind hier System-Accounts die für System Dienste (Datenbanken, Serverprozesse etc.) angelegt wurden. Haben solche Accounts kein oder ein schwaches Passwort, kann sich ein Angreifer mit diesem Konto anmelden.

Es empfiehlt sich daher, die zur Anmeldung erlaubten Konten einzuschränken. Eine Option ist die Angabe individueller Benutzerkonten:

```no-highlight
AllowUsers hansi peterle
```

Alternativ kann man auch alle Benutzer, für die der SSH Zugang erlaubt sein soll, einer Gruppe zuweisen und dann für diese Gruppe die Anmeldung freischalten:

```no-highlight
AllowGrops sshlogin
```

## Deaktivieren der Anmeldung mit Passwort
In der Standard Konfiguration ist der SSH Server so eingestellt, dass Benutzer sich mit Eingabe von Benutzername und Passwort anmelden können. Die Liste der erlaubten Benutzer [lässt sich zwar einschränken](#einschrankung-der-erlaubten-benutzer), jedoch ist die Maschine immer noch anfällig für Brute-Force Angriffe zum Erraten von Benutzer-Passwort Kombinationen.

Einen besseren Schutz vor solchen Angriffen bietet das Login ausschließlich mit SSH Schlüssel. Zum Anmelden muss in dieser Konfiguration jeder Benutzer, der Zugriff auf das System haben soll, einen gültigen SSH Schlüssel besitzen und für den Zugriff konfiguriert haben.

So wird in der Konfigurationsdatei die Passwort-basierte Authentifizierung abgeschaltet:

```no-highlight
PasswordAuthentication no
ChallengeResponseAuthentication no
```

Bevor diese Änderungen in der Konfiguration gemacht werden, sollte natürlich das Login via SSH Schlüssel für mindestens einen Benutzer aktiviert werden. Andernfalls hat man sich selbst ausgesperrt.


