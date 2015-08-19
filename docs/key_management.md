# Schlüsselverwaltung
An dieser Stelle stehen ein paar allgemeine Überlegungen zur Verwaltung von SSH Schlüsseln im Vordergrund. Die Erzeugung von Schlüsseln wird dann [im nächsten Kapitel](keygen.md) erklärt.

## Wie viele Schlüssel?
Es sind verschiedene Ansätze für die Handhabung von SSH Schlüsseln denkbar:

* ein Schlüssel für alle Einsatzzwecke
* ein Schlüssel pro Gruppe entfernter Rechner
* ein Schlüssel je entferntem Rechner

Jeder Ansatz hat verschiedene Vor- und Nachteile.

### Ein Schlüssel für alle Einsatzzwecke
Bei diesem Ansatz ist die Verwaltung des Schlüssels denkbar einfach: es gibt nur einen. Dementsprechend muss man sich auch nur ein Passwort merken. 

Der gravierende Nachteil dieses Ansatzes ist jedoch, dass bei Verlust des einzigen (privaten) Schlüssels gleich alle entfernten Systeme auf einen Schlag kompromittiert sind. Der Austausch gegen einen neuen Schlüssel ist dann sehr aufwändig.

### Ein Schlüssel pro Gruppe entfernter Rechner 
Bei diesem Ansatz lassen sich die entfernten Rechner gruppieren: eine Gruppe wäre z.B. Cloud Rechner (z.B. auf Amazon's EC2), eine andere Gruppe wären Rechner, mit denen man beruflich zu tun hat, etc.

Für jede Gruppe wird ein eigener SSH Schlüssel generiert. Aufgrund der geringen Anzahl von Schlüsseln kommt man auch bei diesem Ansatz wahrscheinlich ohne [explizite Konfiguration](ssh_client.md) des SSH Client aus.

Bei diesem Ansatz gilt jedoch der gleiche Nachteil, wie bei nur einem einzigen SSH Schlüssel: geht der private Schlüssel für eine Gruppe von entfernten Rechnern verloren, sind gleich mehrere Systeme kompromittiert.

### Ein eigener Schlüssel für jeden entfernten Rechner
Bei diesem Ansatz wird für jeden entfernten Rechner ein eigener Schlüssel generiert. Man muß zwar etwas mehr [Arbeit in die Konfiguration des SSH Client](ssh_client.md) stecken, dafür ist bei Verlust des privaten Schlüssels auch genau nur Schlüssel zu tauschen.
