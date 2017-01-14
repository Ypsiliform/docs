Alles zum Thema Mediator:

**Allgemeines**:
- Es sollen mehrere Konfigurationen parallel ausgeführt werden koennen, sodass ein Agent immer auch ueber seinen Konfigurationsnamen identifiziert werden soll
- Der Mediator soll sich zu jeder Verhandlung die beiden Partner, die letzte akzeptierte Loesung und den letzten Vorschlag merken
- Kommunikation per Websockets, da eine bidirektionale Kommunikation notwendig ist

**Von außen aufrufbare Funktionen**:
- add_agent
    - fügt einen neuen Agenten hinzu
    - Agent identifziert sich per ID und Name der Konfiguration
    - Mediator muss sich merken, welcher Agent zu welchem Socket gehoert
- req_negotiation
    - Ein Agent moechte in Verhandlung mit einem anderen Agenten treten
    - Anderer Agent ist nur durch ID gekennzeichnet, Mediator muss das Mapping basierend auf dem Konfigurationsnamen des anfragenden Agenten machen
    - Anzahl der Perioden/Buckets ist variabel und kann explizit angefragt werden
- rec_proposal_feedback
    - Agenten melden, ob sie das vorgeschlagene Proposal akzeptieren

**Interne Funktionen**:
- gen_proposal
    - basierend auf dem letzten Vorschlag soll in der Nachbarschaft ein neuer Vorschlag erzeugt werden
    - Stand jetzt soll dich der Mediator nicht merken, welche Vorschläge er bereits unterbreitet hat!
- send_proposal
    - Der Vorschlag + das letzte akzeptierte Proposal sollen mitgeschickt werden
    - Nach req_negotiation soll der Mediator ein Proposal erzeugen und als gesetzt erachten und direkt ein weiteres Proposal erzeugen, dass dann als das neue Proposal betrachtet wird
- end_negotiation
    - Nach Durchlaufen aller Verhandlungsrunden beendet der Mediator die Verhandlungen
    - Er schickt die letzte von beiden akzeptierte Codierung mit

**Konfiguration**:
- der Mediator bekommt eine zusätzliche URL, über die man die Default-Werte der folgenden Parameter anpassen kann
    - Anzahl Verhandlungsrunden
    - ...

