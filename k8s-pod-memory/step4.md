Was passiert, wenn ein Container über das Limit Speicher anfordert? Wir simulieren
dies mit einem weiteren Pod `cat memory-demo-pod-2.yaml | yq r -C -`{{execute}} indem
der `stress` Befehl weiterhin 150 MB RAM Speicher anfordert, das Limit aber auf 100 MB
reduziert wurde.

Deploye den `memory-demo-pod-2` Pod mit dem Befehl 
`kubectl apply -f memory-demo-pod-2.yaml`{{execute}}. Der `stress` Befehl fordert 150 MB
Speicher, obwohl lediglich 100 MB maximal erlaubt sind.

Betrachte nun den Status des Pods mit `kubectl get pod  memory-demo-pod-2`{{execute}} und
du erhältst folgende Ausgabe
```
NAME                READY   STATUS      RESTARTS   AGE
memory-demo-pod-2   0/1     OOMKilled   1          1m
```

`OOM` steht für **Out of Memory**, das heißt, der Container `memory-demo-container-2`
fordert mehr Speicher an als erlaubt und wird deshalb beendet.   