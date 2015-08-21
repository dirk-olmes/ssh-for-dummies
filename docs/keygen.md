# Schlüsselgenerierung
Zur Erzeugung eines neuen SSH Schlüssels verwendet man den Befehl `ssh-keygen`. Bei Aufruf des Befehls ohne weitere Parameter wird ein Schlüssel mit default-Parametern generiert:

```no-highlight
% ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/hansi/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/hansi/.ssh/id_rsa.
Your public key has been saved in /home/hansi/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:6bi7HDxCG740uFoYpDQ3bIg38sNOhgzxaE40T8Q3WH8 hansi@localhost
The key's randomart image is:
+---[RSA 2048]----+
|.oooo.           |
|o+*o o.          |
|=B+*. .. E       |
|X*+..   ..       |
|+o* o   S        |
| * = + o         |
|. + * = .        |
| . o = +         |
|... . =o         |
+----[SHA256]-----+
```

Bei der Abfrage des Dateinamens muss man aufpassen: gibt man hier nur den Dateinamen und keinen vollständigen Pfad an, wird das Schlüsselpaar im aktuellen Verzeichnis gespeichert.

Man kann einen Schlüssel ohne Passwort generieren, dazu einfach bei der Abfrage des Passworts die Eingabetaste drücken. Dieser Schlüssel ist dann allerdings ungeschützt. Jeder, der den Schlüssel besitzt, kann sich auf dem entfernten System anmelden.