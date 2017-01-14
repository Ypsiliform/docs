# Verhandlungsprotokoll

## Verhandlungsbeginn
Der Agent, der die Primärbedarfe erfüllen soll, beantragt die erste Verhandlung mit dem
zuliefernden Agenten beim Mediator. Der Mediator generiert daraufhin eine erste Referenzlösung.
Diese, sowie eine weiterer Vorschlag werden an beide Agenten geschickt.

## Iterative Verhandlung
Wenn ein Agent einen Vorschlag vom Mediator empfängt, dann bildet er daraus einen Plan, bewertet
diesen und vergleicht die Güte des Plans mit der Güte der Referenzlösung. Die Agenten schicken
ihre Präferenz an den Mediator.

Falls beide die Lösung akzeptieren, so ist dies die neue Referenzlösung. Der Mediator generiert
danach eine neue Lösung und schlägt diese den Agenten vor.

## Ende der Verhandlung
Nach einer bestimmten Anzahl an Iterationen beendet der Mediator die Verhandlung. Der letzte
gemeinsam akzeptierte Lösungsvorschlag ist das Ergebnis der Verhandlung.

## Diagramm
![Sequenzdiagramm der Verhandlung](./Diagramme/Verhandlungsprotokoll.png)
