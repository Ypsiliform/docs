Nachrichtenformate:

Von Agenten:

-	AgentRegistration:

	Key|Value|Beschreibung
	---|-----|------------
	id|int|Eindeutiger Agentnummer innerhalb einer Konfigurationsdatei
	config|String|Bezeichnung der Konfigurationsdatei
	
	Beispiel JSON-codiert Agent 1 aus Konfigdatei "Bsp1":
	```json
	{ 	
		"type"	    : "agentregistration",
		"id"	   : 1,
		"config" 	: "Bsp1"
	}
	```

-	StartNegotiation:
	
	Key|Value|Beschreibung
	---|-----|------------
	agent|int|Agentnummer des Agentens mit dem verhandelt werden soll
	period|int|Anzahl an Perioden / Buckets
	
	Beispiel JSON-codier Agent 1 möchte mit Agent 2 über 12 Perioden verhandeln:
	```json
	{ 	
		"type"	    : "startnegotiation",
		"agent"	 : 2,
		"period" 	 : 12
	}
	```

-	ResponseProposal:

	Key|Value|Beschreibung
	---|-----|------------
	accept|boolean|Vorschlag/Proposal akzeptiert (true) oder abgelehnt (false)

	Agent nimmt Vorschlag an	
	```json
	{ 	
		"type"	    : "responseproposal",
		"accept"	 : true
	}
	```

Von Mediator:

-	SendProposal:

	Key|Value|Beschreibung
	---|-----|------------
	new_proposal|int[]|Neuer Vorschlag/Proposal
	reference_proposal|int[]|Letzter akzeptierter Vorschlag / aktuelle Lösung
	total_rounds|int|Anzahl der Verhandlungsrunden
	remaining_rounds|int|Anzahl der noch ausstehenden Verhandlungen
	
	Mediator sendet ersten Vorschlag für eine Verhandlungsrunde mit 1000 Verhandlungen:
	```json
	{ 	
		"type"	    : "sendproposal",
		"new_proposal"	 : [1,0,1,0,1,0,1,0,1,0,1,0],
		"reference_proposal" : [1,0,1,0,1,0,1,0,1,0,1,0],
		"total_rounds" : 1000,
		"remaining_rounds" : 1000
	}
	```

-	EndNegotiation:
	
	Key|Value|Beschreibung
	---|-----|------------
	solution|int[]|Lösung/Ergebnis der Verhandlung
	
	Mediator sendet das Ergebnis der Verhandlung:
	```json
	{ 	
		"type"	    : "endnegotiation",
		"solution"	 : [1,0,1,0,1,0,1,0,1,0,1,0]
	}
	```

	
Gemeinsame Nachrichten:

-	Error:

	Key|Value|Beschreibung
	---|-----|------------
	error|int|Fehlercode
	
	```json
	{ 	
		"type"	    : "error",
		"error"	 : 1
	}
	
