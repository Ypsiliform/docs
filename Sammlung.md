Sammlung:

Thema: Produzent mind. Zwei Teilezulieferer mit Kapazitäts- Produktionsbeschränkung und Kosten – Simulation – Koordinationsform: Mediator. Mediator liefert Vorschläge
Feststellungen:

-	Jeder Knoten ist ein Agent
-	Restriktion 1: Jeder Bedarf muss just in time voll gedeckt sein (verspätet und nicht liefern ist nicht drin)
-	Restriktion 2: Kapazität ist bei jedem Agenten begrenzt

Name: Ypsiliform

Code-Repository auf Github 

Architektur:
Mediator als Service: Socket mit Jason
Skript liest Datei ein und ruft den Agentencontainer auf
Agenten in einem Container der Mehrere Agenten 

Struktur:
Baum (kein Graph)

Ablauf:

1. Agent 1 schickt dem Mediator den Bedarf nach Verhandlung mit seinem Vorgänger. 

2. Mediator schickt Vorschlag an Agent 1 und 2
3. Wenn die Verhandlungsrunden abgeschlossen sind schickt der Mediator das letzte zugestimmte Ergebnis an Agent 1 und 2 = das beste Ergebnis. 

4. Agent 2 schickt dem Mediator den Bedarf nach Verhandlung mit seinem Vorgänger.  Usw. 

Produktion über die Kapazitätsgrenze: Agent muss ausrechnen wie er vorher optimal produziert haben muss, mit Lagerkosten = immer teurer als just in time Produktion = jedes Problem ist lösbar. 
