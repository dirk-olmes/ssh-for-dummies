# Passwort eines Schlüssels ändern
Das Passwort eines Schlüssels wird mit dem `ssh-keygen` Befehl geändert:

```no-highlight
% ssh-keygen -p -f ~/.ssh/id_rsa
Enter old passphrase:
Enter new passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved with the new passphrase.
```
