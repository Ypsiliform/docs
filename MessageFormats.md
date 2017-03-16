Nachrichtenformate:

Von Agenten:

-	AgentRegistration:

	Key|Value|Beschreibung
	---|-----|------------
	id|int|Eindeutiger Agentnummer innerhalb einer Konfigurationsdatei
	config|String|Bezeichnung der Konfigurationsdatei
	requires|int[]|optionale Nummern der Agent von denen dieser abhängig ist
	demand|int[]|optionaler Bedarf für die 12 Perioden (nur Agent 1)
	
	Beispiel JSON-codiert Agent 1 aus Konfigdatei "Bsp1":
	```json
	{ 	
		"type"	    : "agentregistration",
		"id"	   : 1,
		"config" 	: "Bsp1",
		"requires" : [2,3],
		"demand": [1,2,3,4,5,6,7,8,9,10,11,12]
	}
	```

-	AgentResponse:

	Key|Value|Beschreibung
	---|-----|------------
	selection|int|gewählter Vorschlag
	demands|Map<Int, Int[]>| Bedarf pro Periode für die entsprechende Lösung
	cost|int|Totale Kosten für die gewählte Lösung (Nur für statische Auswertungen, debug-Zwecken und Überprüfung der Lösungsqualität) 
	

	Agent wählt einen Vorschlag und teilt Bedarfe mit
	```json
	{ 	
		"type"	    : "agentresponse",
		"selection" : 1,
		"demands"   : [
			{"solution":1, "demand":[1,2,3,4,5,6,7,8,9,10,11,12]},
			{"solution":2, "demand":[1,2,3,4,5,6,7,8,9,10,11,12]},
			{"solution":3, "demand":[1,2,3,4,5,6,7,8,9,10,11,12]},
			{"solution":4, "demand":[1,2,3,4,5,6,7,8,9,10,11,12]}
		],
		"costs": [138.5, 75.0, 249.925, 217.375]
	}
	```
	
	**obsolete:**
-	StartNegotiation:
	
	Key|Value|Beschreibung
	---|-----|------------
	agent|int|Agentnummer des Agentens mit dem verhandelt werden soll
	period|int|Anzahl an Perioden / Buckets
	
	Beispiel JSON-codier Agent 1 möchte mit Agent 2 über 12 Perioden verhandeln:
	```json
	{ 	
		"type"	 : "startnegotiation",
		"agent"	 : 2,
		"period" : 12
	}
	```


Von Mediator:

-	MediatorRequest:

	Key|Value|Beschreibung
	---|-----|------------
	solutions|Map<Int, Solution>|Neue Wahlvorschläge mit entsprechender Bedarfsanforderung

	
	Mediator sendet Vorschläge aus denen der Agent eine Lösung wählen kann
	```json
	{ 	
		"type"	    : "mediatorrequest",
		"solutions"	 : [
			{"no":1, "solution":[true,false,true,false,true,false,true,false,true,false,true,false], "demands":[10,20,30,40,50,60,70,80,90,100,110,120]},
			{"no":2, "solution":[false,false,true,false,true,false,true,false,true,false,true,false], "demands":[100,20,30,40,50,60,70,80,90,100,110,120]},
			{"no":3, "solution":[true,true,true,false,true,false,true,false,true,false,true,false], "demands":[1,20,30,40,50,60,70,80,90,100,110,120]},
			{"no":4, "solution":[true,false,false,false,true,false,true,false,true,false,true,false], "demands":[10,200,30,40,50,60,70,80,90,100,110,120]}
		]
	}
	```

-	EndNegotiation:
	
	Key|Value|Beschreibung
	---|-----|------------
	solution|boolean[]|Lösung/Ergebnis der Verhandlung
	demands|int[]|Produktionsmengen in der jeweiligen Periode
	
	Mediator sendet das Ergebnis der Verhandlung:
	```json
	{ 	
		"type"	    : "endnegotiation",
		"solution"	 : [true,false,true,false,true,false,true,false,true,false,true,false]
		"demands"	 : [10,200,30,40,50,60,70,80,90,100,110,120]
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
	
